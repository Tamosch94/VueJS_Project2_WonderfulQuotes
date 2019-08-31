<template>
    <div class="container">
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
				this.quotes.push(quoteData);
			},
			deleteQuote(quoteIndex) {
				this.quotes.splice(quoteIndex);
			}
		},
		components: {
			'app-quote-grid': QuoteGrid,
			'app-new-quote': NewQuote
		},

    }
</script>

<style>
</style>
