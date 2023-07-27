<template>
	<div>
		<slot></slot>
	</div>
</template>

<script setup></script>

<style lang="scss" scoped>
	@import "../../scss/variables.scss";

	div {
		width: 75vw;
		height: 75vh;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		border-radius: 1rem;
		box-shadow: 0.2rem 0.2rem 1.2rem rgba($color-black, 0.3);
		background-color: $color-white;
	}
</style>
