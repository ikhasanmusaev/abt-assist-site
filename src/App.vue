<template>
  <div id="app">
    <div class="container">
      <app-header/>
      <app-result-form/>
      <app-result-table/>
      <app-footer/>
    </div>
  </div>
</template>

<script>
  import AppHeader from "./components/AppHeader";
  import AppResultForm from "./components/AppResultForm";
  import AppResultTable from "./components/AppResultTable";
  import AppFooter from "./components/AppFooter";

  export default {
    name: 'App',
    components: {
      AppHeader,
      AppResultForm,
      AppResultTable,
      AppFooter
    }
  }
</script>

<style scoped>
  #app {
    margin: 0;
    font-family: Roboto, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  .container{
    display: flex;
    flex-direction: column;
  }

  /*app-result-form {*/
  /*    justify-self: center;*/
  /*}*/

</style>
