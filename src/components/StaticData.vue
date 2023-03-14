<template>
  <div>
    <hr />
    <h1>Get static data from json</h1>
   <input type="text" v-model="searchValue" placeholder="search">


    <ul>
      <li v-for="beer in usersList2" :key="beer.id">
        {{ beer.name }}
      </li>
    </ul>
  </div>
</template>

<script>

import data from './../assets/data.json'

export default {
  data() {
    return {
      beers: [],
      searchValue: "",
    };
  },

  mounted() {
    this.beers = data;
  },
  computed: {
    usersList2() {
      if (this.searchValue.trim().length > 0) {
        return this.beers.filter((user) => user.name.includes(this.searchValue.trim()))
      }
      return this.beers
    }
  }
};
</script>
