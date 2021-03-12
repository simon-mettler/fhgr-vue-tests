<template>
	<div class="container">
		<div id="app">
			<HelloWorld msg="Hallo Team!"/>
		</div>
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
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
	font-weight: 300;
	font-style: normal;
}
</style>
