<template>
	<Suspense>
		<MainPage></MainPage>
	</Suspense>
</template>

<script setup>
import MainPage from "./components/layout/MainPage.vue"
import { Suspense } from "vue";
</script>

<style lang="scss">
	@import url("https://fonts.googleapis.com/css?family=Lato:100,300,400,700,900");

	* {
		padding: 0;
		box-sizing: inherit;
	}

	html {
		font-size: 62.5%;
	}

	body {
		margin: 0;
		font-family: "Lato", sans-serif;
		font-weight: 400;
		font-size: 1.6rem;
		line-height: 1.7;
		box-sizing: border-box;
	}
</style>
