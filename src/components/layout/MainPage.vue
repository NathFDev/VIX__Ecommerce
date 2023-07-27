<template>
	<BaseSpinner v-if="isLoading"></BaseSpinner>
	<BaseBackground :category="data.category" v-else>
		<BaseCard>
			<ProductItem v-if="valid" v-bind="data" @next="handleNext"></ProductItem>
			<NotFound v-else @next="handleNext"></NotFound>
		</BaseCard>
	</BaseBackground>
</template>

<script setup>
	import BaseBackground from "../UI/BaseBackground.vue";
	import BaseCard from "../UI/BaseCard.vue";
	import BaseSpinner from "../UI/BaseSpinner.vue";
	import ProductItem from "../pages/ProductItem.vue";
	import NotFound from "../pages/NotFound.vue";
	import { computed, ref } from "vue";

	const isLoading = ref(true);

	const data = ref(null);
	const res = await fetch(`https://fakestoreapi.com/products/1`);
	data.value = await res.json();
	isLoading.value = false;

	const count = ref(1);

	const valid = computed(() => {
		if (
			data.value.category === "women's clothing" ||
			data.value.category === "men's clothing"
		)
			return true;
		else return false;
	});

	async function handleNext() {
		isLoading.value = true;
		count.value++;
		if (count.value > 20) count.value = 1;
		const res = await fetch(`https://fakestoreapi.com/products/${count.value}`);
		data.value = await res.json();
		isLoading.value = false;
	}
</script>

<style lang="scss" scoped></style>
