<template>
	<span>
		<the-header></the-header>
		<the-banner></the-banner>
	</span>
</template>

<script>
	import TheHeader from './components/TheHeader.vue'
	import TheBanner from './components/TheBanner.vue'

	export default {

		components: {
			TheHeader,
			TheBanner
		}

	}
</script>

<style>
	body{
		background-color: aliceblue;
	}

</style>