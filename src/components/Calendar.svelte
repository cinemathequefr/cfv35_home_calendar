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


.salle {
  display: inline-block;
  vertical-align: bottom;
  height: 20px;
  width: 20px;
  padding: 0;
  background-position: 50% 50%;
  background-repeat: no-repeat;
  background-color: transparent;
  border: none;
  cursor: pointer;
  transform:  translateY(-2px);
}

.HL {
background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1000 1000'><path fill='%23889' d='M500 0C223.9 0 0 223.9 0 500s223.9 500 500 500 500-223.9 500-500S776.1 0 500 0zM509 719h-99V540.6h-181.4v178.4h-98.6V281h98.7v174.7h181.4v-174.7h99V719zM609.2 719V281h98.7v358h162.2v80H609.2z'/></svg>");
}

.GF {
background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1000 1000'><path fill='%23889' d='M500 0C223.9 0 0 223.9 0 500s223.9 500 500 500 500-223.9 500-500S776.1 0 500 0zM524.3 689.5c-42.8 24.6-95.9 37-159.4 37 -70.5 0-126-19.5-166.6-58.5s-60.9-92.7-60.9-161.1c0-68.8 22.2-124.9 66.6-168.3 44.4-43.4 103.4-65.1 177.1-65.1 46.4 0 87.3 6.4 122.8 19.2v92.5c-33.8-19.5-75.1-29.3-124-29.3 -40.9 0-74.3 13.3-100 39.9 -25.8 26.6-38.6 62.1-38.6 106.4 0 45 11.6 79.8 34.7 104.5 23.1 24.6 54.3 37 93.6 37 23.6 0 42.3-3.4 56.2-10.1v-85.5H338v-78.8h186.3V689.5zM708.1 361.2v107.5h142v80h-142v170.1h-98.7v-438h253.2v80.3H708.1z'/></svg>");
}

.JE {
background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1000 1000'><path fill='%23889' d='M500 0C223.9 0 0 223.9 0 500s223.9 500 500 500 500-223.9 500-500S776.1 0 500 0zM432 541.4c0 58.6-13.6 103.5-40.8 134.7 -27.2 31.2-66.5 46.7-118 46.7 -23 0-44.3-4-63.8-11.9v-92.5c16.9 12.8 35.8 19.2 56.8 19.2 45 0 67.5-33.4 67.5-100.2V277.2H432V541.4zM790.6 715.2H527.9v-438h252.6v80.3H626.6V455h143.2v80H626.6v100.2h164V715.2z'/></svg>");
}




  /* reset */
  /*
  .container,
  .container * {
    color: #000;
    font-size: 1rem;
    text-transform: none;
    font-weight: 400;
    padding-left: 0;
  }
  */
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
              <!-- <span class="salle">{seance.idSalle[0]}</span> -->
              <span class="salle {seance.idSalle[0]}"></span>
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
