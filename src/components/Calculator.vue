<template>
	<h1 class="title">Calculator</h1>
	<main class="calculator">
		<div class="display">
			{{display}}
		</div>
		<div class="buttons">
			<div class="button-row" v-for = "row in buttonRows">
				<div 
				@click="buttonClick(button)"
				:class=" {operator: button.type === 'operator'}"
				class="button" 
				v-for= "button in row">
				{{button.text}}
				</div>
			</div>
		</div>
	</main>
</template>


<script>
export default{
	methods: {
		buttonClick(button) {
			if (button.type == 'number'){
				if (this.previousValue === null){
					this.previousValue = Number(this.display);
					this.display='';
				}
				if (button.text == '.' && this.display.includes('.')) return;
				this.display += button.text;
			} else if (button.text == 'AC') {
				this.display = '';
			}else if (button.text == '+/-') {
				this.display *= -1; 
			} else if (button.text == '=' ){
				this.display = this.operations [this.currentOperator] (+this.previousValue, +this.display);
				this.currentOperator = '';
			} else if (button.type =='operator'){
				if(this.currentOperator) {
				this.display = this.operations [this.currentOperator] (+this.previousValue, +this.display);
				}
				this.previousValue = null;
				this.currentOperator = button.text;
			}
		}
	},
	data:() => ({
		display: '',
		previousValue: '', 
		currentOperator: '',

		operations: {
			'÷': (a, b) => a / b,
			'×': (a, b) => a * b,
			'-': (a, b) => a - b,
			'+': (a, b) => a + b,
			'%': (a, b) => a + b /100,
		},

		buttonRows: [
			[{ 
				text: 'AC', 
				type: 'magic'
			}, { 
				text: '+/-', 
				type:'magic'
			},  { 
				text: '%', 
				type:'operator'
			}, { 
				text: '÷', 
				type:'operator'
			},],
			[{ 
				text: '7', 
				type:'number'
			}, { 
				text: '8', 
				type:'number'
			},  { 
				text: '9', 
				type:'number'
			}, { 
				text: '×', 
				type:'operator'
			},],
			[{ 
				text: '4', 
				type:'number'
			}, { 
				text: '5', 
				type:'number'
			},  { 
				text: '6', 
				type:'number'
			}, { 
				text: '-', 
				type:'operator'
			},],
			[{ 
				text: '1', 
				type:'number'
			}, { 
				text: '2', 
				type:'number'
			},  { 
				text: '3' ,
				type:'number'
			}, { 
				text: '+' ,
				type:'operator'
			},],
			[{ 
				text: '0', 
				type:'number'
			}, { 
				text: '.',
				type:'number'
			},  { 
				text: '=', 
				type:'operator'
			},],
		]
	})

};
</script>


<style>
.title {
	font-size: 1em;
	margin: 0.5em;
	padding: 1em;
}
body {
	width: 100vw;
	height: 100vh;
	font-size: 1.5em;
	display: flex;
	justify-content: center;
	align-items: center;
}
.calculator {
	width: 60vw;
	height: 70vh;
	font-family: sans-serif;
	border-radius: 5px;
	overflow: hidden;
	border: 1px solid deeppink;
}

.display {
	height: 10vh;
	background-color: darkgrey;
	text-align: right;
	color: white;
	font-size: 1.5em;
}

.buttons {
	height: 60vh;
	text-align: center;
}
.button-row {
	height: 20%;
	width: 100%;
	display: flex;
	justify-content: space-around;
	
}
.button {
	display: inline-block;
	outline: 0.5px solid deeppink;
	width: 100%;
/* 	padding: 0.4em; */
	background-color: pink;
	display: flex;
	justify-content: center;
	align-items: center;
}

.operator {
	background-color:salmon;
}

.button:hover {
	background-color: deeppink;
}

</style>