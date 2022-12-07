<template>
	<section class="collapsible">
		<button @click="toggleCollapse" class="collapsible__button">
			<span>{{ title }}</span>
			<span>+++</span>
		</button>

		<div v-if="isCollapsed === false" class="collapsible__content">
			<slot/>
		</div>
	</section>
</template>

<script>
	export default {
		props: {
			title: {
				type: String
			}
		},
		
		data() {
			return {
				isCollapsed: true
			}
		},

		methods: {
			toggleCollapse() {
				this.isCollapsed = !this.isCollapsed;
			}
		}
	}
</script>

<style>
	.collapsible {
		border: 2px solid yellow;
		margin-bottom: 1em;
	}

	.collapsible__button {
		width: 100%;
		cursor: pointer;
		border: 0;
		margin: 0;
		display: flex;
		justify-content: space-between;
	}

	.collapsible__button:hover {
		background: yellow;
		color: black;
	}

	.collapsible__content,
	.collapsible__button {
		padding: 10px;
	}
</style>