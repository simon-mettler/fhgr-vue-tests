<template>
	<div class="container">
		<div id="app">
			<BoolscheOperatoren />
			<div style="height: 100px"></div>
			<Trunkierungen />
		</div>
  </div>
</template>


<script>
import BoolscheOperatoren from './components/BoolscheOperatoren.vue'
import Trunkierungen from './components/Trunkierungen.vue'
export default {
  name: 'App',
  components: {
		BoolscheOperatoren,
		Trunkierungen
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

p {
	font-family: Roboto,sans-serif;
	font-style: normal;
	font-weight: 300;
}


table {
	border-spacing: 0;
	margin: 0 auto;
}

th {
	color: #b39048;
	border-bottom: 2px solid #b39048;
	text-align: left;
	font-weight: 700!important;
}

td, th  {
	font-family: Roboto, sans-serif;
	font-style: normal;
}

td {
	font-weight: 300;
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
