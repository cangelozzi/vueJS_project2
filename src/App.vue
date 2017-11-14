<template>
    <div class="container">
      <appHeader :quoteCount="quotes.length" :maxQuotes="maxQuotes"></appHeader>
      <appNewQuote @quoteAdded="newQuote"></appNewQuote>
      <appQuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></appQuoteGrid>

    <p>Info: Click on a Quote to Delete it!</p>
    </div>
</template>

<script>
  import Header from './components/Header.vue';
  import Quote from './components/Quote.vue';
  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';

  export default {
    data: function(){
      return {
        maxQuotes: 10,
        quotes: ['First Quote']
      }
    },
    components: {
      appHeader: Header,
      appQuote: Quote,
      appQuoteGrid: QuoteGrid,
      appNewQuote: NewQuote
    },

    methods: {
      newQuote(quote) {
        if(this.quotes.length >= this.maxQuotes) {
          return alert('Please delete quote first');
        }
        this.quotes.push(quote);

      },
      deleteQuote(index) {
        this.quotes.splice(index,1);
      }
    }

    }
</script>

<style>
p {
  background-color: yellow;
  text-align: center;
  padding: 20px;
}
</style>
