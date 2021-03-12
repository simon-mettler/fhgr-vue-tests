<template>
	<div class="container">
		<div id="app">
		<Input />

			<table>
				<tr>
					<th></th>
					<th>Suchanfrage</th>
					<th>Anzahl Treffer</th>
					<th>Korrekte Anzahl</th>
				</tr>
				<tr>
					<td>A</td>
					<td><input type="text" v-model.number="inx"></td>
					<td><input type="text" v-model.number="ina"></td>
					<td>{{ sum }}</td>
				</tr>
			</table>

		</div>
  </div>
</template>


<script>

import Input from './components/Input.vue'
export default {
  name: 'App',
  components: {
		Input
  },
	props: {
		ina: {
			type: Number,
			default: 0
		},
		inx: {
			type: Number,
			default: 0
		},
	},
	computed: {
		sum: function() {
			return this.ina + this.inx;
		}
	}


}

</script>


<style>

body {
	background: url(https://blog.fhgr.ch/wp-content/uploads/2018/07/bg-pattern-web_allgem.svg);
  background-color: rgba(0, 0, 0, 0);
  background-attachment: scroll;
	background-attachment: fixed;
	background-color: #f6f6f6;
	margin: 0;
}
.container {
	max-width: 900px;
	border: 1px solid #ecece8;
	margin: 80px auto;
	background: white;
	padding: 100px 20px;
}

</style>
