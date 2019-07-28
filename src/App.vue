<template>
  <div id="app">
    <header class="main-header">
      <h1>Wonderful quotes...</h1>
    </header>
    <div class="container">
      <appHeader :quoteCount="quotes.length" :maxQuotes="maxQuotes"></appHeader>
      <appNewQuote @quoteAdded="newQuote"></appNewQuote>
      <appQuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></appQuoteGrid>
    </div>
    <footer class="main-footer">
      <h1>Footer</h1>
    </footer>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";
export default {
  name: "app",
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },
  data() {
    return {
      quotes: ["Just a quote to see something."],
      maxQuotes: 10
    };
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes)
        return alert("Please delete Quotes first.");
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
*,
::before,
::after {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
html {
  height: 100%;
}
body {
  height: 100%;
  box-sizing: border-box;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  max-width: 100%;
  height: 100%;
}
.main-header {
  text-align: center;
  margin-top: 30px;
}

.main-footer {
  text-align: center;
  background-color: #ccc;
  width: 100%;
  margin-top: auto;
  padding: 25px;
}
</style>
