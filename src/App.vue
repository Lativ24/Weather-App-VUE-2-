<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''">
<main>
  <search-box @search="fetchWeather"></search-box>
  <weather-display :weather="weather"></weather-display>
</main>
  </div>
</template>

<script>
import SearchBox from './components/SearchBox.vue'; 
import WeatherDisplay from './components/WeatherDisplay.vue';
export default {
  name: 'app',
  components: {
    'search-box': SearchBox, 
    'weather-display': WeatherDisplay,
  },
  data(){
    return{
      api_key:'51549e0c5273fe51c515c1a71caa5e95',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query:'',
      weather:{},
    };
  },
  methods:{
    fetchWeather(location){
      
      fetch(`${this.url_base}weather?q=${location}&units=metric&&APPID=${this.api_key}`)
        .then((res) => res.json())
        .then(this.setResults)
      
    },
    setResults(results){
      this.weather=results;
    },
  
  }

}
</script>

<style>
*{
  margin: 0;
  padding:0;
  box-sizing: border-box;
}
body{
  font-family: 'montserrat',sans-serif;
  color: honeydew;
}
#app{
  background-image: url('./assets/cold-bg.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}
#app.warm{
  background-image: url('./assets/warm-bg.jpg');
}
main{
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
}
.search-box{
  width: 100%;
  margin-bottom: 30px;

}
.search-box .search-bar{
  display: block;
  width: 100%;
  padding: 15px;
  
  color: #313131;
  font-size: 20px;

  appearance: none;
  border:none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;

}
.search-box .search-bar:focus{
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}
.location-box .location{
  color: #fff;
  font-size:32px ;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);
}
.location-box .date{
  color: #fff;
  font-size:20px ;
  font-weight: 300;
  font-style: italic;
  text-align: center;
 
}
.weather-box{
  text-align: center;
}
.weather-box .temp{
  display: inline-block;
  padding:10px 25px;
  color: #fff;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0,0,0,0.25) ;
  background-color: rgba(255,255,255,0.25);
  border-radius: 16px;
  margin: 30px 0px;

  box-shadow: 3px 6px rgba(0,0,0,0.25);
}
.weather-box .weather{
  color: #fff;
  font-size: 48px;
  font-weight: 700;
  font-style: italic ;
  text-shadow: 3px 6px rgba(0,0,0,0.25);
}
</style>