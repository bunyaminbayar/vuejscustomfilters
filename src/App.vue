<template>
  <child-component></child-component>
  <filter-custom />
  <multiy-filter />
  <login-page />
  <static-data />
</template>

<script>
import ChildComponent from "./components/ListAndFilter.vue";
import FilterCustom from './components/FilterCustom.vue';
import MultiyFilter from './components/MultiyFilter.vue';
import LoginPage from './components/LoginPage.vue'
import StaticData from './components/StaticData.vue'

export default {
  name: "App",
  components: {
    ChildComponent,
    FilterCustom,
    MultiyFilter,
    LoginPage,
    StaticData,
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
