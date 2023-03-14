<template>
   <h1>Fetch api and filter</h1>
   <input type="text" v-model="searchValue" placeholder="search">
   <ul>
    <li v-for="(beer, index) in usersList2" :key="index">
     {{ index }} {{ beer.name }} - {{ beer.tagline }}
    </li>
   </ul>
   <hr>
</template>

<script>
export default {
  data: () => ({
    searchValue: "",
    users: [],
  }),
    mounted() {
    fetch('https://api.punkapi.com/v2/beers?page=2&per_page=8')
    .then(response => response.json())
    .then(data => {
      this.users = data;
      console.log(this.users);
    });
  },
  computed: {
    usersList2() {
      if (this.searchValue.trim().length > 0) {
        return this.users.filter((user) => user.name.includes(this.searchValue.trim()))
      }
      return this.users
    }
  }
};
</script>

<style>

</style>