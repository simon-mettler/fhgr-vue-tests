<template>
	<div class="hinweis">
		<span
		@mouseover="hover = true"
		@mouseleave="hover = false"
		>?</span>
		<p v-if="hover">{{ hinweis }}</p>
	</div>
</template>


<script>
export default {
  name: 'BoolscheOperatoren',
	data() {
		return {
			hover: false
		}
	},
	props: {
		hinweis: String
	}
}
</script>

<style scoped>
.hinweis {
	display: inline;	
}
</style>

