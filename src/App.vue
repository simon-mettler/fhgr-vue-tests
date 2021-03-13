<template>
	<div class="container">
		<div id="app">
			<BoolscheOperatoren />
		</div>
  </div>
</template>


<script>
import BoolscheOperatoren from './components/BoolscheOperatoren.vue'
export default {
  name: 'App',
  components: {
		BoolscheOperatoren,
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
