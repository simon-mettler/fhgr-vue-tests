<template>
	<div>
	<input v-model="msg" type="text" >
	<p>{{ msg }}</p>
	</div>
</template>

<script>
export default {
  name: 'Input',
	data() {
		return {
			content: 'Simon'
		}
	},
  props: {
    msg: String
  }
}
</script>

<style scoped>
p, td, th {
	font-family: Roboto,sans-serif;
	font-weight: 300;
	font-style: normal;
}
</style>
