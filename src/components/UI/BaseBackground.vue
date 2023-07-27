<template>
	<div
		:class="{
			women: mode === 'women',
			men: mode === 'men',
			none: mode === 'none',
		}"
	>
		<slot></slot>
	</div>
</template>

<script setup>
	import { computed } from "vue";

	const props = defineProps({ category: String });

	const mode = computed(() => {
		if (props.category === "men's clothing") return "men";
		else if (props.category === "women's clothing") return "women";
		else return "none";
	});
</script>

<style lang="scss" scoped>
	@import "../../scss/variables.scss";

	div {
		height: 100vh;
		width: 100vw;
	}

	.women {
		background-image: linear-gradient(
			to bottom,
			$color-light-pink 0%,
			$color-light-pink 65%,
			$color-white 65%
		);
	}

	.men {
		background-image: linear-gradient(
			to bottom,
			$color-light-blue 0%,
			$color-light-blue 65%,
			$color-white 65%
		);
	}

	.none {
		background-image: linear-gradient(
			to bottom,
			$color-light-grey 0%,
			$color-light-grey 65%,
			$color-white 65%
		);
	}
</style>
