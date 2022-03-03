<template>
  <div class="school">
    <h2>学校名称：{{name}}</h2>
    <h2>学校地址：{{addr}}</h2>
  </div>
</template>
<script>
  export default {
    name: 'mySchool',
    data(){
      return {
        name: '张三',
        addr:'北京'
      }

    }

  }
</script>
<style>
.school{
  background-color: palegreen;padding: 5px;
}
</style>