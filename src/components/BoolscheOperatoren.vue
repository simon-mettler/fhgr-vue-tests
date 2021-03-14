<template>

	<table>
		<tr>
			<th></th>
			<th>Suchanfrage</th>
			<th>Anzahl Treffer</th>
			<th>Korrekte Anzahl</th>
		</tr>
		<tr>
			<td>A</td>
			<td><input type="text" v-model="suchanfrage.A"></td>
			<td><input type="text" v-bind:class="{ wrong: treffer.A > 4}" v-model.number="treffer.A"></td>
			<td>-</td>
		</tr>
		<tr>
			<td>B</td>
			<td><input type="text" v-model="suchanfrage.B"></td>
			<td><input type="text" v-model.number="treffer.B"></td>
			<td>-</td>
		</tr>
		<tr>
			<td>C</td>
			<td><input type="text" v-model="suchanfrage.C"></td>
			<td><input type="text" v-model.number="treffer.C"></td>
			<td>-</td>
		</tr>
		<tr>
			<td>D</td>
			<td>{{ suchanfrage.A }} AND {{ suchanfrage.B }}</td>
			<td><input type="text" v-model.number="treffer.D"></td>
			<td>&#8804; {{ calcAND(treffer.A, treffer.B) }} <Hinweis hinweis="Kleinster Wert von A oder B" /></td>
		</tr>
		<tr>
			<td>E</td>
			<td>{{ suchanfrage.A }} AND {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.E"></td>
			<td>&#8804; {{ calcAND(treffer.A, treffer.C) }} <Hinweis hinweis="Kleinster Wert von A oder C" /></td>
		</tr>
		<tr>
			<td>F</td>
			<td>{{ suchanfrage.B }} AND {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.F"></td>
			<td>&#8804; {{ calcAND(treffer.B, treffer.C) }} <Hinweis hinweis="Kleinster Wert von B oder C" /></td>
		</tr>
		<tr>
			<td>G</td>
			<td>{{ suchanfrage.A }} OR {{ suchanfrage.B }}</td>
			<td><input type="text" v-model.number="treffer.G"></td>
			<td>= {{ korrekteAnzahlG }} <Hinweis hinweis="Anzahl A + Anzahl B - Anzahl D" /></td>
		</tr>
		<tr>
			<td>H</td>
			<td>({{ suchanfrage.A }} AND {{ suchanfrage.B }}) OR {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.H"></td>
			<td>= {{ korrekteAnzahlH }} <Hinweis hinweis="Anzahl D + Anzahl C - Anzahl E - Anzahl F" /></td>
		</tr>
		<tr>
			<td>I</td>
			<td>{{ suchanfrage.A }} AND {{ suchanfrage.B }} OR {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.I"></td>
			<td>= {{ korrekteAnzahlI }} <Hinweis hinweis="Normalerweise Anzahl H" /></td>
		</tr>
		<tr>
			<td>J</td>
			<td>{{ suchanfrage.A }} AND ({{ suchanfrage.B }} OR {{ suchanfrage.C }})</td>
			<td><input type="text" v-model.number="treffer.J"></td>
			<td>= {{ korrekteAnzahlJ }} <Hinweis hinweis="Anzahl D + Anzahl E - Anzahl F" /></td>
		</tr>
	</table>

</template>


<script>
import Hinweis from './Hinweis.vue'
export default {
  name: 'BoolscheOperatoren',
  components: {
		Hinweis	
  },
	data() {
		return {
			suchanfrage: {
				A: 'Haus',
				B: 'Boot',
				C: 'Wasser'
			},
			treffer: {
				A: '',
				B: '',
				C: '',
				D: '',
				E: '',
				F: '',
				G: '',
				H: '',
				I: '',
				J: ''
			}
		}
	},
	computed: {
		korrekteAnzahlG() {
			return this.treffer.A + this.treffer.B - this.treffer.D;
		},
		korrekteAnzahlH() {
			return this.treffer.C + this.treffer.D - this.treffer.E - this.treffer.F;
		},
		korrekteAnzahlI() {
			return this.treffer.H + 0; // +0 makes sure that at least 0 is displayed...
		},
		korrekteAnzahlJ() {
			return this.treffer.D + this.treffer.E - this.treffer.F;
		}
	},
	methods: {
		calcAND(num1, num2) {
			return Math.min(num1, num2);
		}
	}
}
</script>


<style scoped>

.wrong {
	background-color: red;
}

table {
	border-spacing: 0;
	margin: 0 auto;
}

td, th  {
	font-family: Roboto,sans-serif;
	font-style: normal;
	font-weight: 300;
}

td:nth-child(1){
	width: 22px;
	padding-left: 5px;
	color: #b39048;
	font-weight: 700;
}

td:nth-child(2) {
	min-width: 220px;
}

td:nth-child(3) {
	width: 150px;
}

td:nth-child(4) {
	width: 130px;
	padding-left: 10px;
}

th {
	color: #b39048;
  border-bottom: 2px solid #b39048;
	text-align: left;
	font-weight: 700;
}

input {
	border: none;
	font-size: 1em;
	background: #f4eee3;
	height: 25px;
	padding-left: 5px;
	display:table-cell; 
	width: calc(100% - 6px);
	font-family: Roboto, sans-serif;
	font-weight: 300;
}

</style>
