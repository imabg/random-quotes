<template>
  <div id="app">
    <div id="heading"></div>
    <p class="display-1">Random Quotes</p>
    <rndmQuote :myQuote = "quote"></rndmQuote>
     <button class="btn btn-outline-success" style="margin: 25px" @click = "generateQuote">Quote</button>
    <button class="btn btn-outline-primary" style="margin: 25px" @click = "tweetMe"><i class="fab fa-twitter"> Tweet</i></button>
    <div class="alert alert-primary" role="alert">
        Crafted By: <a href="https://github.com/abhay676" target="_blank">Abhay Goswami</a>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import rndmQuote from './components/renderQuote.vue';

export default {
  name: 'app',
  components: {
    rndmQuote
  },
  data() {
    return {
      quote: ''
    }
  },
  created() {
      axios
      .get('https://talaikis.com/api/quotes/random/')
      .then(response =>{
        this.quote = response;
        });
  },
  methods: {
    generateQuote() {
       axios
      .get('https://talaikis.com/api/quotes/random/')
      .then(response =>{
        this.quote = response;
        });
    },
    tweetMe() {
      let query = this.quote.data.quote;
       window.open(`https://twitter.com/intent/tweet?text=${query}`);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h2 {
  font-size: 55px;
  font-weight: bold;
}
</style>
