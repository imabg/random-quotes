<template>
  <div>
    <div class="cat">
      <label >Category: </label>
      <span> {{myQuote.data.cat}}</span>
    </div>
    <div class="quote">
      <span id="rndmQuote">{{myQuote.data.quote}}</span>
      <div class="author">
        <label>By {{myQuote.data.author}}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    myQuote: {
      required: true
    }
    }
  }
</script>

<style scoped>
  .cat {
    font-weight: bold;
    font-size: 15px;
    margin-top: 22px;
    text-align: right;
  }
  .quote {
    border: 1px solid black;
    box-shadow: 1px 2px 2px #ccc;
    margin: auto;
  }
  #rndmQuote {
    font-family: 'Pattaya', sans-serif;
    font-size: 25px;
  }
  .author{
    font-family: 'Cedarville Cursive', cursive;
    font-size: 25px;
  }
</style>
