<template>
	<div id="secondChild">
		<!-- 平级组件之间的通信传值 -->
		<h2>secondChild组件</h2>
		<p>从平级组件firstChild传过来的值：{{msg}}</p>
		<i>vue axios的运用</i>
		<table>
			<tbody>
				<tr v-for="item in datainfo">
					<td>{{item.customerId}}</td>
					<td>{{item.contactName}}</td>
					<td>{{item.companyName}}</td>
					<td>{{item.phone}}</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script type="text/javascript">
import bus from '../assets/enentBus.js'
	export default{
		data(){
			return {
				msg:"morenzhi",
				datainfo:[]
			}
		},
		mounted(){
			var self = this;
			bus.$on("userEvent",function(msg){
				self.msg = msg
			})
			this.postData()
		},
		methods:{
			postData:function(){
				// debugger
				var self = this;
				this.$http.get("http://211.149.193.19:8080/api/customers").then(function(res){
					// console.log(res)
					self.datainfo = res.data
					console.log(self.datainfo)
				}).catch(function(err){
					console.log(err)	
				})
			}
		}
	}
</script>

<style type="text/css">
	td{
		border: 1px solid #ddd;
		padding: 5px;
	}
</style>