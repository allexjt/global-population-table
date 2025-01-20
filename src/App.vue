<template>
<div class="container">
  <Header title="Global Population Data" />
  <Dropdown @change="changeDate($event)" :years="years" />
  <BarChart :populationData="populationData" title="Population per Country*" :year="currentYear"/>
  <Footer text="*Per 1 Million **Graph is scaled by log10" size="normal" />
  <Footer text="Developed by Jacob Allex-Buckner" size="small" />
</div>
</template>

<script>
import Header from './components/Header.vue'
import Dropdown from './components/Dropdown.vue'
import BarChart from './components/BarChart.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Dropdown,
    BarChart,
    Footer,
  },
  data() {
    return {
      years: [],
      populationData: [],
      currentYear: "1960",
    }
  },
  methods: {
    /* Fetching data from API */
    async fetchPopulationData() {
      const res = await fetch('https://pkgstore.datahub.io/JohnSnowLabs/population-figures-by-country/population-figures-by-country-csv_json/data/2159fad77778c3b584f3d396593e0af6/population-figures-by-country-csv_json.json')
      const data = await res.json()
      return data;
    },
    changeDate(event) {
      this.currentYear = event.target.value
    }
  },
  async created() {
    document.title = "Global Population";
    /* Setting up valid year range */
    var years = [];
    var i;
    for (i = 1960; i <= 2016; i++) {
      years.push(i);
    }
    this.years = years;
    this.populationData =  await this.fetchPopulationData()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 250px;
  border: 1px solid steelblue;
  padding: 30px;
  padding-bottom: 20px;
  border-radius: 5px;
}
</style>
