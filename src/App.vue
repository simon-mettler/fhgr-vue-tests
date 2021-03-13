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
					<td><input type="text" v-model="rowA.suchanfrage"></td>
					<td><input type="text" v-bind:class="{ wrong: rowA.treffer > 4}" v-model.number="rowA.treffer"></td>
					<td>-</td>
				</tr>
				<tr>
					<td>B</td>
					<td><input type="text" v-model="rowB.suchanfrage"></td>
					<td><input type="text" v-model.number="rowB.treffer"></td>
					<td>-</td>
				</tr>
				<tr>
					<td>C</td>
					<td><input type="text" v-model="rowC.suchanfrage"></td>
					<td><input type="text" v-model.number="rowC.treffer"></td>
					<td>-</td>
				</tr>
				<tr>
					<td>D</td>
					<td>{{ rowA.suchanfrage }} AND {{ rowB.suchanfrage }}</td>
				</tr>
				<tr>
					<td>{{ minValue(rowA.treffer, rowB.treffer) }}</td>
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
	data: function() {
	return {
		rowA: {
			suchanfrage: 'Haus',
			treffer: ''},
		rowB: {
			suchanfrage: 'Boot',
			treffer: ''},
		rowC: {
			suchanfrage: 'Wasser',
			treffer: ''},
		}
	},
	methods: {
		minValue(num1, num2) {
			if(num1 && num2) {
				return Math.min(num1, num2);
			} else {
				return 0;
			}
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

p, td, th {
	font-family: Roboto,sans-serif;
	font-weight: 300;
	font-style: normal;
}

.wrong {
background-color: red;
}

</style>
