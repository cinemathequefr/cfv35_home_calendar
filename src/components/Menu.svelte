<script>

</script>

<style>
  body {
    position: relative;
    margin: 0;
    font-family: "Source Sans Pro";
    background-color: #fff;
    color: #111;
  }

  .container {
    width: 1140px;
    margin: 0 auto;
  }

  .header {
    position: relative;
    color: #fff;
    background: #1e2345;
    background: linear-gradient(90deg, #161a33 0%, #414d8c 100%);
  }

  .header > .container {
    position: relative;
    height: 210px;
  }

  /* .header a {
    text-decoration: none;
    color: inherit;
  } */

  .logo {
    position: absolute;
    width: 425px;
    height: auto;
    top: 55px;
  }

  input[type="text"] {
    font-family: "Source Sans Pro";
    background-color: transparent;
    border-radius: 2px;
    border: none;
    margin: 0;
    padding: 12px 12px;
    color: #111;
    font-weight: 300;
    font-size: 16px;
    min-width: 400px;
  }

  .search-container {
    position: absolute;
    border-radius: 2px;
    background-color: #eee;
    padding: 0;
    top: 83px;
    right: 0;
    width: 476px;
    transition: 0.2s;
  }

  .search-container:focus-within {
    background-color: #fff;
  }

  .search {
    display: inline-block;
    border: none;
    background-repeat: no-repeat;
    background-position: 100% 50%;
    padding-right: 60px;
    width: 428px;
  }

  .search-button {
    display: inline-block;
    vertical-align: middle;
    height: 44px;
    width: 44px;
    padding: 0;
    background-position: 50% 50%;
    background-repeat: no-repeat;
    background-color: transparent;
    border: none;
    background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='48' height='48' viewBox='0 0 48 48'><path fill='%23999' d='M29.54 23.89c0-1.56-0.56-2.89-1.66-3.99s-2.44-1.66-3.99-1.66 -2.89 0.55-3.99 1.66 -1.66 2.44-1.66 4 0.55 2.89 1.66 3.99c1.11 1.11 2.44 1.66 4 1.66s2.89-0.56 3.99-1.66C28.98 26.77 29.54 25.44 29.54 23.89zM36 34.39c0 0.44-0.16 0.82-0.48 1.14C35.2 35.84 34.82 36 34.39 36c-0.45 0-0.83-0.16-1.13-0.48l-4.33-4.31c-1.51 1.04-3.18 1.56-5.03 1.56 -1.2 0-2.35-0.23-3.45-0.7 -1.1-0.47-2.04-1.1-2.84-1.89 -0.79-0.79-1.43-1.74-1.89-2.84C15.23 26.24 15 25.09 15 23.89s0.23-2.35 0.7-3.45c0.47-1.1 1.1-2.04 1.89-2.84 0.8-0.79 1.74-1.43 2.84-1.89C21.53 15.23 22.68 15 23.89 15s2.35 0.23 3.45 0.7c1.1 0.47 2.05 1.1 2.84 1.89 0.8 0.8 1.43 1.74 1.89 2.84 0.47 1.1 0.7 2.25 0.7 3.45 0 1.85-0.52 3.53-1.56 5.04l4.33 4.33C35.84 33.56 36 33.94 36 34.39z'/></svg>");
    cursor: pointer;
  }

  ul.menu1 {
    white-space: nowrap;
    position: absolute;
    bottom: -5px;
    right: 0;
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  ul.menu1 > li {
    display: inline-block;
  }
  ul.menu1 > li > a {
    display: block;
    color: #fff;
    background-color: #7a5b42;
    margin: 0 0 0 -1px;
    padding: 8px 8px;
    font-family: Quicksandcf;
    font-weight: 700;
    font-size: 1rem;
    text-transform: uppercase;
    transition: 0.2s;
  }

  ul.menu1 > li > a:hover,
  ul.menu1 > li > a:active {
    background-color: rgb(142, 111, 86);
  }

  ul.menu2 {
    white-space: nowrap;
    position: absolute;
    top: 4px;
    right: 0;
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  ul.menu2 > li {
    display: inline-block;
  }
  ul.menu2 > li > a {
    display: block;
    margin: 0 4px;
    padding: 0 0 0 0;
    border-bottom: solid 2px transparent;
    font-size: 0.938rem;
    transition: 0.1s;
    color: #9ca1bd;
  }

  ul.menu2 > li > a:hover,
  ul.menu2 > li > a:active {
    border-bottom-color: #9ca1bd;
    /* border-bottom-color: rgba(255, 255, 255, 0.5); */
  }

  .lang {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background: transparent;
    font-size: 0.875rem;
    font-weight: 400;
    border: none;
    padding-bottom: 0px;
    border-bottom: solid 2px #fff;
    text-align: center;
    color: #fff;
  }

  .vVzemXxY_0 {
    stroke-dasharray: 539 541;
    stroke-dashoffset: 540;
    animation: vVzemXxY_draw 2000ms ease 0ms forwards;
  }
  .vVzemXxY_1 {
    stroke-dasharray: 320 322;
    stroke-dashoffset: 321;
    animation: vVzemXxY_draw 2000ms ease 90ms forwards;
  }
  .vVzemXxY_2 {
    stroke-dasharray: 593 595;
    stroke-dashoffset: 594;
    animation: vVzemXxY_draw 2000ms ease 181ms forwards;
  }
  .vVzemXxY_3 {
    stroke-dasharray: 545 547;
    stroke-dashoffset: 546;
    animation: vVzemXxY_draw 2000ms ease 272ms forwards;
  }
  .vVzemXxY_4 {
    stroke-dasharray: 672 674;
    stroke-dashoffset: 673;
    animation: vVzemXxY_draw 2000ms ease 363ms forwards;
  }
  .vVzemXxY_5 {
    stroke-dasharray: 520 522;
    stroke-dashoffset: 521;
    animation: vVzemXxY_draw 2000ms ease 454ms forwards;
  }
  .vVzemXxY_6 {
    stroke-dasharray: 432 434;
    stroke-dashoffset: 433;
    animation: vVzemXxY_draw 2000ms ease 545ms forwards;
  }
  .vVzemXxY_7 {
    stroke-dasharray: 620 622;
    stroke-dashoffset: 621;
    animation: vVzemXxY_draw 2000ms ease 636ms forwards;
  }
  .vVzemXxY_8 {
    stroke-dasharray: 545 547;
    stroke-dashoffset: 546;
    animation: vVzemXxY_draw 2000ms ease 727ms forwards;
  }
  .vVzemXxY_9 {
    stroke-dasharray: 597 599;
    stroke-dashoffset: 598;
    animation: vVzemXxY_draw 2000ms ease 818ms forwards;
  }
  .vVzemXxY_10 {
    stroke-dasharray: 599 601;
    stroke-dashoffset: 600;
    animation: vVzemXxY_draw 2000ms ease 909ms forwards;
  }
  .vVzemXxY_11 {
    stroke-dasharray: 545 547;
    stroke-dashoffset: 546;
    animation: vVzemXxY_draw 2000ms ease 1000ms forwards;
  }
  @keyframes vVzemXxY_draw {
    100% {
      stroke-dashoffset: 0;
    }
  }
  @keyframes vVzemXxY_fade {
    0% {
      stroke-opacity: 1;
    }
    94.44444444444444% {
      stroke-opacity: 1;
    }
    100% {
      stroke-opacity: 0;
    }
  }
</style>

<div class="header">
  <div class="container">
    <svg class="logo" viewBox="0 0 1100 245">
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M106.34,195.13L68.81,195.13L50,176.52L50,82.61L68.81,63.81L106.34,63.81L125.16,82.62L125.16,110.8L96.98,110.8L96.98,91.98L78.17,91.98L78.17,167.14L96.98,167.14L96.98,148.32L125.16,148.32L125.16,176.51Z"
        class="vVzemXxY_0" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        width="28.17"
        height="131.6"
        d="M140.2 50.36 L168.37 50.36 L168.37 181.95999999999998 L140.2
        181.95999999999998 Z"
        class="vVzemXxY_1" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M230.41,195.18L211.6,142.76L211.6,195.18L183.43,195.18L183.43,63.76L211.6,63.76L230.41,116.43L230.41,63.76L258.59,63.76L258.59,195.18Z"
        class="vVzemXxY_2" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M273.64,194.89L273.64,63.57L339.43,63.57L339.43,91.74L301.81,91.74L301.81,115.24L339.43,115.24L339.43,143.41L301.81,143.41L301.81,166.9L339.43,166.9L339.43,194.89Z"
        class="vVzemXxY_3" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M420.28,194.89L420.28,148.09L401.47,194.89L382.65,148.09L382.65,194.89L354.48,194.89L354.48,63.57L382.65,63.57L401.47,110.56L420.28,63.57L448.45,63.57L448.45,194.89Z"
        class="vVzemXxY_4" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M515.21 181.42L512 162.6H488.32l-3.21
        18.81h-27.99l24.32-131.59h37.54l24.41 131.59h-28.17l0 0H515.21zM500.16
        93.6l-6.88 40.83h13.86L500.16 93.6 500.16 93.6z"
        class="vVzemXxY_5" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M595.1,91.74L595.1,194.89L566.92,194.89L566.92,91.74L538.66,91.74L538.66,63.57L623.27,63.57L623.27,91.74Z"
        class="vVzemXxY_6" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M679.71,194.89L679.71,143.41L660.9,143.41L660.9,194.89L632.72,194.89L632.72,63.57L660.9,63.57L660.9,115.24L679.71,115.24L679.71,63.57L707.89,63.57L707.89,194.89Z"
        class="vVzemXxY_7" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M722.93,194.89L722.93,63.57L788.74,63.57L788.74,91.74L751.1,91.74L751.1,115.24L788.74,115.24L788.74,143.41L751.1,143.41L751.1,166.9L788.74,166.9L788.74,194.89Z"
        class="vVzemXxY_8" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M822.59 194.71l-18.81-18.62V82.18l18.81-18.8h37.53l18.81
        18.8v84.54l-9.36 9.35h16.89v18.64h-63.88l0 0 0 0H822.59zM850.76
        91.56h-18.81v75.16h18.81V91.56z"
        class="vVzemXxY_9" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M950.34,181.95L912.81,181.95L893.99,163.14L893.99,50.36L922.16,50.36L922.16,153.78L940.98,153.78L940.98,50.36L969.15,50.36L969.15,163.14Z"
        class="vVzemXxY_10" />
      <path
        fill="none"
        stroke="#fff"
        stroke-width="4"
        d="M984.2,194.89L984.2,63.57L1050,63.57L1050,91.74L1012.37,91.74L1012.37,115.24L1050,115.24L1050,143.41L1012.37,143.41L1012.37,166.9L1050,166.9L1050,194.89Z"
        class="vVzemXxY_11" />
    </svg>

    <ul class="menu1">
      <li>
        <a href="javascript: void 0;">Cinéma</a>
      </li>
      <li>
        <a href="javascript: void 0;">Exposition</a>
      </li>
      <li>
        <a href="javascript: void 0;">Musée</a>
      </li>
      <li>
        <a href="javascript: void 0;">Bibliothèque</a>
      </li>
      <li>
        <a href="javascript: void 0;">Magazine</a>
      </li>
      <li>
        <a href="javascript: void 0;">Jeune public</a>
      </li>
      <li>
        <a href="javascript: void 0;">Infos pratiques</a>
      </li>
      <li>
        <a href="javascript: void 0;">Calendrier</a>
      </li>
    </ul>

    <ul class="menu2">
      <li>
        <a href="javascript: void 0;">Nos collections</a>
      </li>
      <li>
        <a href="javascript: void 0;">Groupes et collectivités</a>
      </li>
      <li>
        <a href="javascript: void 0;">Actions en milieu scolaire</a>
      </li>
      <li>
        <a href="javascript: void 0;">Presse</a>
      </li>
      <li>
        <a href="javascript: void 0;">Événements privés</a>
      </li>
      <li>
        <select class="lang">
          <option value="fr" selected>Fr</option>
          <option value="en">En</option>
        </select>
      </li>
    </ul>
    <div class="search-container">
      <input class="search" type="text" placeholder="Chercher sur le site" />
      <button class="search-button" />
    </div>
  </div>
</div>
