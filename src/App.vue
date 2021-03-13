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
					<td><input type="text" v-model="boolA1"></td>
					<td><input type="text" v-model.number="boolA2"></td>
					<td>-</td>
				</tr>
				<tr>
					<td>B</td>
					<td><input type="text" v-model="boolB1"></td>
					<td><input type="text" v-model.number="boolB2"></td>
					<td>-</td>
				</tr>
				<tr>
					<td>C</td>
					<td><input type="text" v-model="boolC1"></td>
					<td><input type="text" v-model.number="boolC2"></td>
					<td>-</td>
				</tr>
				<tr>
					<td>D</td>
					<td>{{ boolA1 }} AND {{ boolB1 }}</td>
					<td><input type="text" v-model.number="boolD2"></td>
					<td>≤ {{ boolD3 }}</td>
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
		boolA1: {
			type: String,
			default: "Haus"
		},
		boolA2: {
			type: Number
		},
		boolB1: {
			type: String,
			default: "Boot"
		},
		boolB2: {
			type: Number
		},
		boolC1: {
			type: String,
			default: "Wasser"
		},
		boolC2: {
			type: Number
		},
		boolD2: {
			type: Number
		},
	},
	computed: {
		boolD3: function() {
			if(this.boolA2 && this.boolB2) {
				return Math.min(this.boolA2, this.boolB2);
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

</style>
