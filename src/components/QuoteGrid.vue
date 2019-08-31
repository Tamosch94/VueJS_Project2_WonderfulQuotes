// Holds all Quotes
<template lang="html">
	<div class="row">
		<!-- You can use click.native modifier to get the native  HTML element of the component-->
		<app-quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">
			{{ quote }}
		</app-quote>
	</div>
</template>

<script>
	import Quote from './Quote.vue';

	export default {
			props: ['quotes'],
			components: {
				'app-quote': Quote,
			},
			methods: {
				deleteQuote(quoteIndex) {
					this.$emit('quoteDeleted', quoteIndex);
				}
			}
	}
</script>

<style lang="css" scoped>
</style>
