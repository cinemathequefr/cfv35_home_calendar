<script>
  import { onMount } from "svelte";
  import { artTitre } from "../lib/format";
  import dayjs from "dayjs";
  dayjs.locale("fr");
  import "../lib/dayjs_custom_locale_fr.js";
  export let data = [];

  console.log(window.location.hash);

  // onMount(async () => {
  // console.log(JSON.stringify(data, null, 2));
  // });
</script>

<style>
  section {
    background-color: #ccc;
    margin: 0;
  }

  .cols {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: space-between;
    align-content: flex-start;
    align-items: stretch;
  }

  .col {
    order: 0;
    flex: 0 1 auto;
    align-self: auto;
    width: 25%;
    margin: 1px;
    /* background-color: #ccc; */
    background: linear-gradient(to top, #ccc 0%, #eee 100%);
  }

  a.seance {
    display: block;
    color: inherit;
    font-size: 1rem;
    padding: 8px;
    margin: 1px;
    transition: 0.15s;
  }

  a.seance:hover,
  a.seance:active {
    background-color: #bbb;
  }

  .titre {
    font-weight: 600;
  }
  .cycle {
    text-transform: uppercase;
    font-size: 0.875rem;
  }
</style>

<section>
  <div class="container" style="margin-top:0; margin-bottom: 0;">

    <div class="cols">
      {#each data as col}
        <div class="col">
          {#each col as seance}
            <a class="seance" href="javascript:void 0;">
              {dayjs(seance.dateHeure).format('HH[h]mm')} {seance.idSalle[0]}
              <div class="cycle">{seance.cycle}</div>
              <ul>
                {#each seance.items as item}
                  <li>
                    <div class="titre">{artTitre(item.art, item.titre)}</div>
                    {item.realisateurs || ''} {item.annee || ''}
                  </li>
                {/each}
              </ul>
            </a>
          {/each}
        </div>
      {/each}
      <div class="col extra" />
    </div>
  </div>
</section>
