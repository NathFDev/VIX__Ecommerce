<template>
	<div class="container">
		<div class="product__image">
			<img :src="image" alt="product image" />
		</div>
		<div class="product__details">
			<p class="product__title" :class="'product__title--' + mode">
				{{ title }}.
			</p>
			<div class="product__rating">
				<span>{{ category }}</span>
				<div class="product__rate" :class="'product__rate--' + mode">
					<span>{{ rating.rate }}/5</span>
					<div class="product__star-rating"></div>
					<div class="product__star-rating"></div>
					<div class="product__star-rating"></div>
					<div class="product__star-rating"></div>
					<div class="product__star-rating"></div>
				</div>
			</div>
			<p class="product__info">
				{{ description }}
			</p>
			<div class="product__price" :class="'product__price--' + mode">
				<p>${{ price }}</p>
				<button class="product__order" :class="'product__order--' + mode">
					Buy now
				</button>
				<button
					class="product__next"
					:class="'product__next--' + mode"
					@click="
						emit('next');
						handleClick();
					"
				>
					Next Product
				</button>
			</div>
		</div>
	</div>
</template>

<script setup>
	import { computed, watch, onMounted } from "vue";

	const emit = defineEmits(["next"]);

	const props = defineProps({
		title: String,
		price: Number,
		description: String,
		category: String,
		image: String,
		rating: Object,
	});

	const mode = computed(() => {
		if (props.category === "men's clothing") return "men";
		else if (props.category === "women's clothing") return "women";
		else return "none";
	});

	function handleClick() {
		const rating = document.querySelectorAll(".product__star-rating");
		const className = "active--" + mode.value;
		rating.forEach((i, idx) => {
			i.classList.value = "";
			i.classList.add("product__star-rating");
			if (idx < Math.ceil(props.rating.rate)) {
				i.classList.add(className);
			}
		});
	}

	onMounted(() => {
		const rating = document.querySelectorAll(".product__star-rating");
		const className = "active--" + mode.value;
		rating.forEach((i, idx) => {
			i.classList.value = "";
			i.classList.add("product__star-rating");
			if (idx < Math.ceil(props.rating.rate)) {
				i.classList.add(className);
			}
		});
	});
</script>

<style lang="scss" scoped>
	@import "../../scss/variables.scss";

	.container {
		display: flex;
		padding: 1rem;
		width: 100%;
		height: 100%;
		justify-content: space-evenly;
		overflow: hidden;
	}

	button {
		width: 48%;
		display: inline-block;
		font-size: inherit;
		border-radius: 3px;
		padding: 0.5rem;
		box-shadow: 1px 1px 2px $color-dark-grey;

		&:hover,
		&:active {
			cursor: pointer;
		}

		&:not(:last-child) {
			margin-right: 2rem;
		}
	}

	.product {
		&__image {
			flex: 30%;
			display: flex;
			justify-content: center;
			align-items: center;

			img {
				max-height: 90%;
				max-width: 90%;
				object-position: top;
			}
		}

		&__details {
			flex: 50%;
			padding-right: 3rem;
		}

		&__rate {
			display: flex;
			align-items: center;

			span {
				margin-right: 5px;
			}

			.active {
				&--men {
					background-color: $color-dark-blue;
				}

				&--women {
					background-color: $color-purple;
				}
			}

			div {
				border-radius: 50%;
				display: inline-block;
				width: 1.4rem;
				height: 1.4rem;
			}

			&--women {
				div {
					border: 1px solid $color-purple;
				}
			}

			&--men {
				div {
					border: 1px solid $color-dark-blue;
				}
			}
		}

		&__title {
			font-size: 2.4rem;
			font-weight: 700;
			margin: inherit;
			margin: 1rem 0;

			&--women {
				color: $color-purple;
			}

			&--men {
				color: $color-dark-blue;
			}
		}

		&__rating {
			display: flex;
			justify-content: space-between;
			font-weight: 300;
			border-bottom: 1px solid $color-light-grey;
			font-size: 1.4rem;
		}

		&__info {
			font-weight: 300;
			height: 35%;
			overflow: scroll;
		}

		&__price {
			border-top: 1px solid $color-light-grey;

			p {
				font-size: 2.4rem;
				font-weight: 700;
				margin: inherit;
			}

			&--men {
				p {
					color: $color-dark-blue;
				}
			}

			&--women {
				p {
					color: $color-purple;
				}
			}
		}

		&__order {
			color: $color-white;

			&--women {
				background-color: $color-purple;
				border: 1px solid $color-purple;
			}

			&--men {
				background-color: $color-dark-blue;
				border: 1px solid $color-dark-blue;
			}
		}

		&__next {
			background-color: $color-white;

			&--women {
				border: 2px solid $color-purple;
				color: $color-purple;
			}

			&--men {
				border: 2px solid $color-dark-blue;
				color: $color-dark-blue;
			}
		}
	}
</style>
