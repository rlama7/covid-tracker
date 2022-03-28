<template>
  <main class="home">
    Hello World
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  components: {},
  data(){
    return{
      loading:true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif')
    }
  },
  methods:{
    async fetchCovidData(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    }
  },
  async created(){
    const data = await this.fetchCovidData()
    // console.log(data)
    this.dataDate = data.dataDate
    this.stats = data.Global
    this.countries = data.countries
    this.loading = false
  }
}
</script>