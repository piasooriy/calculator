<template>
	<section class="converter">
		<input class="converter__input" type="number" placeholder="C" v-model="valueCelcius" />
		<div class="converter__output">{{ valueFahrenheit }} F</div>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				valueCelcius: 10,
			}
		},

		computed: {
			valueFahrenheit() {
				return (this.valueCelcius * 1.8) + 32;
			}
		}
	}
</script>

<style>
	.converter {
		display: flex;
	}

	.converter__input {
		background: inherit;
		color: inherit;
		border: 1px solid white;
		padding: 10px;
		margin: 5px;
	}

	.converter__output {
		border: 1px solid gray;
		padding: 10px;
		margin: 5px;
	}
</style>