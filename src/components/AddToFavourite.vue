<template>
  <div>Add To Favourite City</div>
</template>

<script>
export default {
    name:'Add to Favourite City',
     data () {
    return {
      api_key:'e71c2b2a7d6700a136b1ccc4cb362cc1',
      url_base:'https://api.openweathermap.org/data/2.5/',
      query:'',
      weather:{}
    }

  },
  methods: {
    fetchWeather (e) {
      if(e.key == "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();


          }).then(this.setResults);
      }
    },
    FavouriteCity(){
  
    let city = ['Pune'];

    console.log(city.length);
    }
  }



}
</script>

<style>

</style>

//  test 12345