<template>
  <div>
    <hr />
    <h1>Fetch api and multy filter</h1>

 <label for="ph-select">PH Değeri:</label>
    <select id="ph-select" v-model="selectedPh">
      <option disabled value="">PH Seçin</option>
      <option v-for="ph in phValues" :key="ph.id" :value="ph">{{ ph }}</option>
    </select>

    <label for="abv-select">ABV Değeri:</label>
    <select id="abv-select" v-model="selectedAbv">
      <option disabled value="">ABV Seçin</option>
      <option v-for="abv in abvValues" :key="abv.id" :value="abv">{{ abv }}</option>
    </select>

    <label for="search-input">Arama:</label>
    <input id="search-input" v-model="searchQuery" />

    <ul>
      <li v-for="beer in filteredBeers" :key="beer.id">
        {{ beer.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      beers: [],
      selectedPh: '',
      selectedAbv: '',
      searchQuery: '',
    };
  },

  computed: {
    phValues() {
      const phValues = this.beers.map((beer) => beer.ph);
      return [...new Set(phValues)];
    },

    abvValues() {
      const abvValues = this.beers.map((beer) => beer.abv);
      return [...new Set(abvValues)];
    },

    filteredBeers() {
      let filtered = this.beers;

      if (this.selectedPh) {
        // Seçili PH değerine göre filtreleme yapın
        filtered = filtered.filter((beer) => beer.ph === this.selectedPh);
      }

      if (this.selectedAbv) {
        // Seçili ABV değerine göre filtreleme yapın
        filtered = filtered.filter((beer) => beer.abv === this.selectedAbv);
      }

      if (this.searchQuery) {
        // Arama sorgusuna göre filtreleme yapın
        const query = this.searchQuery.toLowerCase();
        filtered = filtered.filter(
          (beer) =>
            beer.name.toLowerCase().includes(query) ||
            beer.tagline.toLowerCase().includes(query) ||
            beer.description.toLowerCase().includes(query)
        );
      }

      return filtered;
    },
  },

  mounted() {
    fetch('https://api.punkapi.com/v2/beers?page=2&per_page=8')
      .then((response) => response.json())
      .then((data) => {
        this.beers = data;
      });
  },
};
</script>
