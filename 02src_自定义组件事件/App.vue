      <template>
      <div class="app">
        <h1>{{msg}}</h1>
        <h1>{{studentName}}</h1>
        <my-school></my-school>
<!--        <my-student @wzh="abcd"></my-student>-->
        <my-student ref="student"></my-student>
      </div>
      </template>

      <script>
      import mySchool from "@/components/School";
      import myStudent from "@/components/Student";
        export default {
          name:'App',
          components:{myStudent,mySchool},
          data(){
            return{
              msg:'德玛西亚',
              studentName:''
            }
          },
          methods:{
            abcd(name){
              console.log(name)
              this.studentName=name
            }
          },
          mounted() {
            this.$refs.student.$on('wzh',this.abcd)
            // this.$refs.student.$once('wzh',this.abcd)
            // 只触发一次
            // 谁触发wzh事件，this就是谁
          }
        }
      </script>

      <style>
        .app{
          background-color: beige;
        }
      </style>
