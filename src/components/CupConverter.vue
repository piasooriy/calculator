<!-- tutorial from this legend " https://www.youtube.com/watch?v=MRsDx3sFKOs&ab_channel=CodingGarden"
 -->
<template>
	<h1 class="title">Cup converter</h1>
	<section class="cupConverter">
		<input class="cup_input" type="number" v-model="cupValue">
		<div class="output_section">
			<div class="output output_ounces">{{ouncesValue}} oz</div>
			<br>
			<div class="output output_milliliter">{{milliliterValue}} ml</div>
			<br>
			<div class="output output_liter">{{deciliterValue}} dl</div>
			<br>
			<div class="output output_grams">{{gramsValue}} g</div>
		</div>
	</section>
</template>

<script>
	export default {
		data () {
			return {
				cupValue: 1,
			}
		}, 

	//Here I have added the formula to convert cups to each unit
	// which I think is right, in computed, I have the 
	//output-values, and return works in a way where the cup-values
	//entered, will be returned based on the formula to convert
	//in the case of ounces it is cup * 8. 
	//I think this is right
	computed: {
		ouncesValue() {
			return (this.cupValue * 8);
		},

		milliliterValue() {
			return (this.cupValue * 237);
		},

		deciliterValue() {
			return (this.cupValue * 23.7);
		},

		gramsValue() {
			return (this.cupValue * 200);
		},
		
	}	
	}

</script>

<style>
.title {
	font-size: 1em;
	justify-items: center;
}
section {
	background-color: pink;
	width: 60vw;
	height: 30vh;
	display: flex;
	justify-content: space-between;
	align-items: center;
	border: 1px solid deeppink;
}

.cup_input {
	background-color: inherit;
	border: none;
	height: 30vh;
	width: 20vw;
	border: 1px solid deeppink;
	font-size: 1em;
	justify-items: center;


}

.output_section {
	display: grid;
	grid-template-columns: repeat(1, 1fr);
	width: 30vw;
	justify-items: center;
}

.output {
	background-color: inherit;
}



</style>