<script>
  import { onMount } from "svelte";
  import { artTitre, join } from "../lib/format";
  import _ from "lodash";
  import dayjs from "dayjs";
  dayjs.locale("fr");
  import "../lib/dayjs_custom_locale_fr.js";
  export let curDate;
  export let data = [];
</script>

<style>
  section {
    margin: 0;
    background-color: #ddd;
  }

  section > .container {
    margin-top: 0;
    margin-bottom: 0;
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
    padding-top: 8px;
    border-right: solid 3px #fff;
  }

  .col:last-child {
    border-right-color: transparent;
  }

  .date {
    display: block;
    font-size: 1.25rem;
    font-weight: 600;
    color: #336;
    padding: 0 0 12px 4px;
  }

  a.seance {
    display: block;
    color: inherit;
    font-size: 1rem;
    padding: 0 8px 8px 4px;
    transition: 0.1s;
  }

  a.seance:hover,
  a.seance:active {
    background-color: #ccc;
  }

  .dateheure {
    display: inline-block;
    color: #262680;
    /* color: #336; */
    font-size: 1.25rem;
    font-weight: 600;
  }

  .salle {
    display: inline-block;
    color: #262680;
    /* color: #336; */
    font-size: 1rem;
    font-weight: 600;
  }

  .cycle {
    text-transform: uppercase;
    font-size: 0.938rem;
    font-weight: 400;
  }

  .mention {
    color: #000;
  }

  li {
    margin: 2px 0;
    padding-left: 6px;
    border-left: solid 3px transparent;
    /* border-left: solid 3px #bfbfcc; */
  }

  .titre {
    color: #262680;
  }

  .film-infos {
    font-size: 0.875rem;
  }
</style>

<section>
  <div class="container">
    <div class="cols">
      {#each data as col, i}
        <div class="col">
          {#if i === 0}
            <div class="date">
              {_.capitalize(dayjs(curDate).format('dddd D MMMM YYYY'))}
            </div>
          {/if}
          {#each col as seance}
            <a class="seance" href="javascript:void 0;">
              <span class="dateheure">
                {dayjs(seance.dateHeure).format('HH[h]mm')}
              </span>
              <span class="salle">{seance.idSalle[0]}</span>
              <span class="cycle">{seance.cycle}</span>
              {#if seance.mention}
                <div class="mention">{seance.mention}</div>
              {/if}
              <ul>
                {#if seance.titreEvenement}
                  <li class="titre">{seance.titreEvenement}</li>
                {:else}
                  {#each seance.items as item}
                    <li>
                      <div class="titre">{artTitre(item.art, item.titre)}</div>
                      <div class="film-infos">
                        {join(', ', [item.realisateurs, item.annee])}
                      </div>
                    </li>
                  {/each}
                {/if}
              </ul>
            </a>
          {/each}
        </div>
      {/each}
      <div class="col extra" />
    </div>
  </div>
</section>
