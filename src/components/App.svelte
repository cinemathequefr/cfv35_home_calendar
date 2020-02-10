<script>
  import { onMount } from "svelte";
  import _ from "lodash";
  import Menu from "./Menu.svelte";
  import Calendar from "./Calendar.svelte";
  import dayjs from "dayjs";
  // dayjs.locale("fr");
  // import "../lib/dayjs_custom_locale_fr.js";

  let data = [];
  let dayData = [];

  let curDate = dayjs()
    .startOf("day")
    .format("YYYY-MM-DD");

  $: dayData = _(data)
    .groupBy(d => d.dateHeure.substring(0, 10))
    .pick(curDate)
    .values()
    .flatten()
    .map(d => {
      return _({})
        .assign(d, { slot: timeSlotFn(d.dateHeure.substring(11, 15)) })
        .value();
    })
    // Fonction pour distribuer les séances dans un tableau à 3 cases selon la valeur de slot
    .reduce(
      (acc, v) => {
        let i = _.indexOf(["07:00", "17:00", "20:00"], v.slot);
        acc[i] = _.concat(acc[i], [v]);
        return acc;
      },
      [[], [], []]
    );

  const timeSlotFn = createTimeSlotFn(["07:00", "17:00", "20:00"]);

  onMount(async () => {
    const res = await fetch(
      "https://gist.githubusercontent.com/nltesown/28c230ed63550a77062a560d632f7e63/raw/calendar_65_67.json"
      // "https://raw.githubusercontent.com/cinemathequefr/Publications_cycles/master/data/PROG67%20Mars-mai%202020/PROG67%20Mars-mai%202020_CALENDAR.json"
    );

    data = await res.json();
  });

  function changeDate(e) {
    curDate = dayjs(curDate)
      .startOf("day")
      .add(e < 0 ? -1 : 1, "days")
      .format("YYYY-MM-DD");
  }

  /**
   * createTimeSlotFn
   * A partir d'un tableau représentant un découpage horaire de la journée (créneaux), crée une fonction renvoyant le créneau dans lequel se trouve une heure
   * @param {Array:string} Tableau *ordonné* d'heures de début de créneau (ex. : ["07:00", "13:00", "15:00", "17:00", "19:00", "21:00", "23:00"])
   * @return {Function}
   */
  function createTimeSlotFn(ts) {
    var mts = _(ts)
      .map(hhmm => dayjs(`1900-01-01T${hhmm}`))
      .value();
    return function(hhmm) {
      var found;
      var o = _(mts).reduceRight(function(acc, i) {
        return found ? found : !i.isAfter(acc) ? (found = i) : acc;
      }, dayjs(`1900-01-01T${hhmm}`));
      if (!found) o = _.last(mts); // If the input time is before the first slot, then it goes to the last (for late night shows)
      return o.format("HH:mm");
    };
  }
</script>

<style>
  .selector {
    position: fixed;
    right: 0;
    bottom: 0;
    margin: 0;
    display: inline-block;
    background-color: #223;
  }
  input[type="date"] {
    margin: 4px;
    height: 38px;
    padding: 6px 10px;
    background-color: #fff;
    border-radius: 0;
    box-shadow: none;
    box-sizing: border-box;
  }
</style>

<Menu />
<Calendar data={dayData} {curDate} />

<div
  class="selector"
  on:DOMMouseScroll={e => {
    changeDate(e.deltaY);
    e.preventDefault();
  }}
  on:wheel={e => {
    changeDate(e.deltaY);
    e.preventDefault();
  }}>
  <input type="date" bind:value={curDate} />
</div>
