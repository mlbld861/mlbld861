<template>
  <div class="demo">
<!--    ref-->
    <H1>{{msg}}</H1>
    <h2>学生名称：{{name}}</h2>
    <h2>学生性别：{{sex}}</h2>
    <h2>学生年龄：{{age+1}}</h2>
  </div>
</template>
<script>
  export default {
  name:'myStudent',
  data() {
    return {
      msg:'我是一个学生',

    }
  },
    // props:['name','age','sex']  简单接收
    // props:{
    // name:String,
    //   age:Number,
    //   sex:String
    // }
    props:{
    name:{
      type:String,
      required:true
    },
      age:{
      type:Number,
        default:99
      },
      sex:{
      type:String,
        required:true
      }
    }
}

</script>
<style>
.demo{
  background-color: aqua;
}
</style>