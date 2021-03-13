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
					<td><input type="text" v-model.number="rowD.treffer"></td>
					<td>&#8804; {{ calcAND(rowA.treffer, rowB.treffer) }}</td>
				</tr>
				<tr>
					<td>E</td>
					<td>{{ rowA.suchanfrage }} AND {{ rowC.suchanfrage }}</td>
					<td><input type="text" v-model.number="rowE.treffer"></td>
					<td>&#8804; {{ calcAND(rowA.treffer, rowC.treffer) }}</td>
				</tr>
				<tr>
					<td>F</td>
					<td>{{ rowB.suchanfrage }} AND {{ rowC.suchanfrage }}</td>
					<td><input type="text" v-model.number="rowF.treffer"></td>
					<td>&#8804; {{ calcAND(rowB.treffer, rowC.treffer) }}</td>
				</tr>
				<tr>
					<td>G</td>
					<td>{{ rowA.suchanfrage }} OR {{ rowB.suchanfrage }}</td>
					<td><input type="text" v-model.number="rowG.treffer"></td>
					<td>= {{ korrekteAnzahlG }}</td>
				</tr>
				<tr>
					<td>H</td>
					<td>({{ rowA.suchanfrage }} AND {{ rowB.suchanfrage }}) OR {{ rowC.suchanfrage }}</td>
					<td><input type="text" v-model.number="rowH.treffer"></td>
					<td>= {{ korrekteAnzahlH }}</td>
				</tr>
				<tr>
					<td>I</td>
					<td>{{ rowA.suchanfrage }} AND {{ rowB.suchanfrage }} OR {{ rowC.suchanfrage }}</td>
					<td><input type="text" v-model.number="rowI.treffer"></td>
					<td>= {{ korrekteAnzahlI }}</td>
				</tr>
				<tr>
					<td>J</td>
					<td>{{ rowA.suchanfrage }} AND ({{ rowB.suchanfrage }} OR {{ rowC.suchanfrage }})</td>
					<td><input type="text" v-model.number="rowJ.treffer"></td>
					<td>= {{ korrekteAnzahlJ }}</td>
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
	data() {
		return {
			rowA: {
				suchanfrage: 'Haus',
				treffer: ''
			},
			rowB: {
				suchanfrage: 'Boot',
				treffer: ''
			},
			rowC: {
				suchanfrage: 'Wasser',
				treffer: ''
			},
			rowD: {
				treffer: ''
			},
			rowE: {
				treffer: ''
			},
			rowF: {
				treffer: ''
			},
			rowG: {
				treffer: ''
			},
			rowH: {
				treffer: ''
			},
			rowI: {
				treffer: ''
			},
			rowJ: {
				treffer: ''
			},
		}
	},
	methods: {
		calcAND(num1, num2) {
			if(num1 && num2) {
				this.korrekt = 88;
				return Math.min(num1, num2);
			} else {
				return 0;
			}
		}
	},
	computed: {
		korrekteAnzahlG() {
			return this.rowA.treffer + this.rowB.treffer - this.rowD.treffer;
		},
		korrekteAnzahlH() {
			return this.rowC.treffer + this.rowD.treffer - this.rowE.treffer - this.rowF.treffer;
		},
		korrekteAnzahlI() {
			return this.rowH.treffer + 0; // +0 makes sure that at least 0 is displayed...
		},
		korrekteAnzahlJ() {
			return this.rowD.treffer + this.rowE.treffer - this.rowF.treffer;
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
