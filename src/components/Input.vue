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
</style>
