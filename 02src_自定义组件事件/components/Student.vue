<template>
  <div class="student">
    <h2>学生名称：{{name}}</h2>
    <h2>学生性别：{{sex}}</h2>
    <button @click="getSchoolName">点我传递学生姓名</button>
    <button @click="unbind">点我解绑</button>
  </div>
</template>
<script>
  export default {
    name: 'myStudent',
    data(){
      return {
        name: '张三',
        sex:'男'
      }
    },
    methods:{
      getSchoolName(){
          this.$emit('wzh',this.name)
      },
      unbind(){
        this.$off()
      }
    }


  }
</script>
<style>
.student{
  background-color: aqua;
  padding: 5px;
}
</style>