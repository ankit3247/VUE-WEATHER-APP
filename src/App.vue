<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text" class="search-box" placeholder="Search for a city..." v-model="query" @keypress="fetchWeather"/>
             </div>
             <div class="weather-wrap" v-if="typeof weather.main !='undefined'">
               <div class="location-box">
                 <div class="location">{{weather.name}},{{weather.sys.country }}</div>
                 <div class="date">{{ dateBuilder()}}</div>
               </div>

               <div class="weather-box">
                 <div class="temp">{{Math.round(weather.main.temp)}}°C</div>
                 <div class="weather">{{weather.weather[0].main}}</div>
               </div>
              
                <div class="favourite-city"> 
                <button type="button" class="btn btn-primary" v-on:click="addcity">Add City!!!</button> 
                {{message}}
                </div>  

                
               
              

                 
              
                
                
                
                
               
              
               

             </div>
    </main>
  </div>
</template>

<script>






export default {

  name: 'App',
  


 
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
    setResults (results) {
      this.weather = results;

    },
    dateBuilder(){
      let d = new Date();
      let months =["January","February","March","April","May","June","July","August","September","October","November","December"];
      let days =["Sunday","Monday","Tuesday","Wednesday","Thrusday","Friday","Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;

    },

   
    

   

  },

  myApp= new Vue({
    el:'#app',
    data:{
      message:'Favourite City'
    },
    methods:{
      addcity:function(){
        alert('Favourite City');
      }
    },
  }),







  

  


  



 



 

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montserrat',sans-serif;
}

#app {
  background-image:url('https://cdn.pixabay.com/photo/2015/03/26/09/47/sky-690293__480.jpg');
  background-size:cover;
  background-position: bottom;
  transition: 0.4s;
}



main {
  min-height:120vh;
  min-width: 100vh;
  padding: 50px;
  /* background-image: linear-gradient(to bottom,rgba(0,0,0,0.25),rgba(0,0,0,0.75));  */
}

.search-box {
  width:100%;
  height:700%;
  margin-bottom:100px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  height: 100%;
  padding: 15px;
  color: #313131;
  font-size:20px;
  appearance: none;
  border:none;
  outline: none;
  background: none;
  background-color: rgba(255,255,255,0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
  box-shadow:0px 0px 8px rgba(0,0,0,0.25);
}

.search-box .search-bar:box {
  background-color: rgba(255,255,255,0.75);
  box-shadow:0px 0px 16px rgba(0,0,0,0.25);
  border-radius:16px 0px 16px 0px;  
}

.location-box .location {
  color:#FFF;
  font-size:32px;
  font-weight:500;
  text-align:center;
  text-shadow:1px 3px rgba(0,0,0,0.25);
}

.location-box .date {
  color:#FFF;
  font-size:20px;
  font-weight:300;
  font-style:italic;
  text-align:center;
}

.weather-box {
  text-align:center;
}

.weather-box .temp {
  display:inline-block;
  padding:10px 25px;
  color:#FFF;
  font-size:102px;
  font-weight:900;
  text-shadow:3px 6px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.25);
  border-radius: 16px;
  margin:30px 0px;
  box-shadow:3px 6px rgba(0,0,0,0.25);
}

.weather-box .weather {
  color:#FFF;
  font-size:48px;
  font-weight:700;
  font-style:italic;
  text-shadow:3px 6px rgba(0,0,0,0.25);
   
}



</style>

Vue.component('favorite', {
    template: '#template-favorite',
    data: function() {
        return { };
    },
    props: {
        'name': {
            type: String,
            default: 'favorite'
        },
        'value': {
            type: Boolean,
            default: false
        },
        'disabled': {
            type: Boolean,
            default: false
        }
    },
    methods: {
        favorite: function() {
            if (this.disabled==true) {
                return;
            }
            this.value = !this.value;
        }
    }
});


var app = new Vue({
   el: 'body'
});



<!-- test 123 -->

<!-- test 1234 -->

 <!-- texting 12345678980 -->

