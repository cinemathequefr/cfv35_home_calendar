<script>
  import { onMount } from "svelte";
  import _ from "lodash";
  import Menu from "./Menu.svelte";
  import Calendar from "./Calendar.svelte";
  import dayjs from "dayjs";
  // dayjs.locale("fr");
  // import "../lib/dayjs_custom_locale_fr.js";

  let data = [];
  let curDate = "2020-04-25";
  // const curDate = "2020-03-09";
  // const curDate = "2020-03-14";

  const timeSlotFn = createTimeSlotFn(["07:00", "17:00", "20:00"]);

  onMount(async () => {
    const res = await fetch(
      "https://raw.githubusercontent.com/cinemathequefr/Publications_cycles/master/data/PROG67%20Mars-mai%202020/PROG67%20Mars-mai%202020_CALENDAR.json"
    );

    data = await res.json();

    data = _(data)
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
  });

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

<Menu />
<Calendar {data} />
