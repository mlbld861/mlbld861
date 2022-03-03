<template>
  <div >
    <my-student></my-student>
    <my-school></my-school>
  </div>
</template>

<script>
      import mySchool from "@/components/School";
      import myStudent from "@/components/Student";
	export default {
		name:'App',
    components:{mySchool,myStudent}
  }
</script>

<style>
</style>
