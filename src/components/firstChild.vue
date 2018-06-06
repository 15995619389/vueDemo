<template>
	<div id="firstChild">
		<h2>firstChild组件</h2>
		<button type="button" v-on:click="sendMsg">向平级组件传值</button>
	</div>
</template>

<script type="text/javascript">
	import bus from "../assets/enentBus.js";
	export default {
		methods:{
			sendMsg:function(){
				bus.$emit("userEvent","我是向平级组件传值的信息")
			}
		}
	}
</script>

<style type="text/css">
	
</style>