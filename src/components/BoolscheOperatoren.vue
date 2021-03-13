<template>

	<table>
		<tr>
			<th><Hinweis /></th>
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
			<td>&#8804; {{ calcAND(treffer.A, treffer.B) }}</td>
		</tr>
		<tr>
			<td>E</td>
			<td>{{ suchanfrage.A }} AND {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.E"></td>
			<td>&#8804; {{ calcAND(treffer.A, treffer.C) }}</td>
		</tr>
		<tr>
			<td>F</td>
			<td>{{ suchanfrage.B }} AND {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.F"></td>
			<td>&#8804; {{ calcAND(treffer.B, treffer.C) }}</td>
		</tr>
		<tr>
			<td>G</td>
			<td>{{ suchanfrage.A }} OR {{ suchanfrage.B }}</td>
			<td><input type="text" v-model.number="treffer.G"></td>
			<td>= {{ korrekteAnzahlG }}</td>
		</tr>
		<tr>
			<td>H</td>
			<td>({{ suchanfrage.A }} AND {{ suchanfrage.B }}) OR {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.H"></td>
			<td>= {{ korrekteAnzahlH }}</td>
		</tr>
		<tr>
			<td>I</td>
			<td>{{ suchanfrage.A }} AND {{ suchanfrage.B }} OR {{ suchanfrage.C }}</td>
			<td><input type="text" v-model.number="treffer.I"></td>
			<td>= {{ korrekteAnzahlI }}</td>
		</tr>
		<tr>
			<td>J</td>
			<td>{{ suchanfrage.A }} AND ({{ suchanfrage.B }} OR {{ suchanfrage.C }})</td>
			<td><input type="text" v-model.number="treffer.J"></td>
			<td>= {{ korrekteAnzahlJ }}</td>
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
