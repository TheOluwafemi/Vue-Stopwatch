<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
  #app {
    font-family: 'Roboto', Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #fff;
    box-sizing: border-box;
    font-size: 16px;
    background: #212121;
  }

  // reset to normalize browser styles
  *,
  *:before,
  *:after {
    box-sizing: inherit;
  }

  body,
  h1,
  h2,
  h3,
  h4,
  h5,
  h6,
  p {
    margin: 0;
    padding: 0;
    font-weight: normal;
  }
</style>
