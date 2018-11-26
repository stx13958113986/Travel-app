<template>
   <div>
        <city-header></city-header>
        <city-search :city="cities"></city-search>
        <city-list :city="cities" :hot="hotCities" :letter="letter"></city-list>
        <city-alphabet :city="cities" @change="handleChange"></city-alphabet>
   </div>
</template>
<script>
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      cities: {},
      hotCities: [],
      letter: ''
    }
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then((response) => {
          this.cities = response.data.data.cities
          this.hotCities = response.data.data.hotCities
        })
        .catch((error) => {
          console.log(error)
        })
    },
    handleChange (letter) {
      this.letter = letter
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>
<style lang="stylus" scoped>
</style>
