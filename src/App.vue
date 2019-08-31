<template>
    <div class="container">
		<app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
		<app-new-quote @quoteAdded="newQuote"></app-new-quote>
		<app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
		<div class="row">
			<div class="col-sm-12 text-center">
				<div class="alert alert-info">
					Info: Click on a quote to delete it
				</div>
			</div>
		</div>
    </div>
</template>

<script>
	import QuoteGrid from './components/QuoteGrid.vue';
	import NewQuote from './components/NewQuote.vue';
	import Header from './components/Header.vue';

    export default {
    	data: function() {
			return {
				quotes: [
					'Just one quote to see something'
				],
				maxQuotes: 10
			}
		},
		methods: {
			newQuote(quoteData) {
				if (this.quotes.length >= this.maxQuotes) {
					return alert("Ups! You reached the maximum amount of quotes, delete some quotes first!!");
				}
				this.quotes.push(quoteData);
			},
			deleteQuote(quoteIndex) {
				this.quotes.splice(quoteIndex, 1);
			}
		},
		components: {
			'app-header': Header,
			'app-quote-grid': QuoteGrid,
			'app-new-quote': NewQuote
		},

    }
</script>

<style>
</style>
