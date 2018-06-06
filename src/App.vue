<template>
  <div id="app">
    <!--静态传值  -->
    <!-- <child msg="父组件向子组件--静态传值"></child> -->
    <!-- 动态传值 -->
    <child :msg="(parentmsg,info)"></child>

    <!-- 子组件向父组件传值 -->
    <child v-on:list="show">{{text}}</child>
    
    //平级组件传值
    <first></first>
    <second></second>
  </div>
</template>

<script>
  import child from "./components/child"
  import first from "./components/firstChild"
  import second from "./components/secondChild"
export default {
  name: 'App',
  data(){
    return {
      text:"",
      parentmsg:"父组件向子组件-动态-传值",
      info:`
        a:子组件在props中创建一个属性，用以接收父组件传过来的值
        b:父组件中注册子组件
        c:在子组件标签中添加子组件props中创建的属性
        d:把需要传给子组件的值赋给该属性`
    }
  },
  components:{
    child,
   first,
   second
  },
  methods:{
    show:function(data){
      console.log(data)
      this.text = data
    }
  }
}
</script>

<style>

</style>
