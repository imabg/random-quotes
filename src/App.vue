<template>
  <div id="app">
    <h2>Random Quotes</h2>
    <rndmQuote :myQuote = "quote"
      :renderQuote = "renderQuote"
    ></rndmQuote>
    <button class="btn btn-outline-success" style="margin: 25px" @click = "generateQuote">Quote</button>
    <button class="btn btn-primary" style="margin: 25px" v-if = "renderQuote" @click = "tweetMe"><i class="fab fa-twitter"> Tweet</i></button>
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
      quote: '',
      renderQuote: false
    }
  },
  methods: {
    generateQuote() {
      axios
      .get('https://talaikis.com/api/quotes/random/')
      .then(response =>{
        this.quote = response;
        });
        this.renderQuote = true;
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
}

</style>
