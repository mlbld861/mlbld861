<template>
  <div class="student">
    <h2>学生名称：{{name}}</h2>
    <h2>学生性别：{{sex}}</h2>
    <button @click="sendInfo">德玛西亚</button>
  </div>
</template>
<script>
  export default {
    name: 'myStudent',
    data(){
      return {
        name: '张三',
        sex:'男',
      }
    },
    methods:{
      sendInfo(){
        this.$bus.$emit('infoPass',this.name)
      }
    },
    beforeDestroy() {
      this.$bus.$off('off')
    }


  }
</script>
<style>
.student{
  background-color: aqua;
  padding: 5px;
}
</style>