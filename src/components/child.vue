<template>
	<div>
		<h2>child子组件部分</h2>
		<p>{{msg}}</p>
		<button type="button" v-on:click="send">向父组件传值</button>
	</div>
</template>

<script type="text/javascript">
	export default{
		props:["msg"],
		methods:{
			send:function(){
				this.$emit("list","我是从子组件传值过来的")
			}
		}
	}
</script>

<style type="text/css">
	
</style>