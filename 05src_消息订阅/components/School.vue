<template>
  <div class="school">
    <h2>学校名称：{{name}}</h2>
    <h2>学校地址：{{addr}}</h2>
    <h2>学生的名字：{{sname}}</h2>
  </div>
</template>
<script>
  import pubsub from 'pubsub-js'
  export default {
    name: 'mySchool',
    data(){
      return {
        name: '新东方烹饪学校',
        addr:'北京',
        sname:''
      }
    },
    mounted() {

       this.pubId= pubsub.subscribe('hello',(msgName,data)=>{
       this.sname=data
     })
    },
    beforeDestroy() {
      pubsub.unsubscribe(this.pubId)
    }

  }
</script>
<style>
.school{
  background-color: palegreen;padding: 5px;
}
</style>