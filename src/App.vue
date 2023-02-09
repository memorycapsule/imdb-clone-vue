<template>
  <header>
    <div class="row">
      <div class="column">
        <img src="https://i.imgur.com/M7pwMya.png" class="imdb-logo" />
      </div>
      <div class="column"></div>
    </div>
  </header>

  <main>
    <router-view />
  </main>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;

  &::selection {
    background-color: transparentize($color: #282828, $amount: 0.5);
  }
  body {
    background-color: #000000;
  }
  a {
    text-decoration: none;
  }

  .column {
    float: left;
    justify-content: space-between;
    width: 50%;
  }
  .row:after {
    content: "";
    display: table;
    clear: both;
  }
  header {
    padding: 10px 16px;
    background-color: #121212;
    box-shadow: 0 0 6px rgba($color: #000000, $alpha: 0.1);
  }
  .imdb-logo {
    width: auto;
    height: 50px;
  }
}
</style>
