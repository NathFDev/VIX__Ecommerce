<template>
	<div class="container">
		<div>
			<p>This product is unavailable to show</p>
			<button @click="emit('next')">Next Product</button>
		</div>
	</div>
</template>

<script setup>
	const emit = defineEmits(["next"]);
</script>

<style lang="scss" scoped>
	@import "../../scss/variables.scss";

	.container {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
		background-color: $color-white;
		overflow: hidden;
	}

	div {
		text-align: center;
		width: 40%;
	}

	p {
		margin: 0;
		margin-bottom: 1rem;
	}

	button {
		background-color: $color-white;
		border: 2px solid $color-black;
		color: $color-black;
		padding: 0.5rem;
		width: 100%;
		cursor: pointer;
	}
</style>
