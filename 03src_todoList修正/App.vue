<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <MyHeader
               :receive="receiver"></MyHeader>
       <MyList :todos="todos"
               :checkTodo="checkTodo"
               :deleteTodo="deleteTodo"></MyList>
       <MyFooter :todos="todos"
                 @checkAllTodo="checkAllTodo"
                 @clearTodos="clearTodos"></MyFooter>
      </div>
    </div>
  </div>
</template>

<script>
  import MyList from "@/components/MyList";
  import MyFooter from "@/components/MyFooter";
  import MyHeader from "@/components/MyHeader";
	export default {
		name:'App',
    components: {MyFooter, MyList, MyHeader},
    props:['receive'],
    data(){
      return{
        todos:JSON.parse(localStorage.getItem('todos'))
      }
    },
    methods:{
      receiver(one){
            this.todos.unshift(one)
      },
      checkTodo(id){
          this.todos.forEach((todo)=>{
            if (todo.id===id)todo.done=!todo.done
          })
      },
      deleteTodo(id){
        this.todos=this.todos.filter(todo=>{return todo.id!==id})
      },
      checkAllTodo(x){
        this.todos.forEach((todo)=>{
          todo.done=x
        })
      },
      clearTodos(){
          this.todos=this.todos.filter((todo=>{
            return !todo.done
          }))
      }
    },
    watch:{
      todos:{
        immediate:true,
        deep:true,
          handler(newValue){
            localStorage.setItem('todos',JSON.stringify(newValue)) ||[]
          }
      }
    }
    // 监视函数前面参数是新值，后面的是旧值
  }
</script>

<style>
      /*base*/
      body {
        background: #fff;
      }

      .btn {
        display: inline-block;
        padding: 4px 12px;
        margin-bottom: 0;
        font-size: 14px;
        line-height: 20px;
        text-align: center;
        vertical-align: middle;
        cursor: pointer;
        box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
        border-radius: 4px;
      }

      .btn-danger {
        color: #fff;
        background-color: #da4f49;
        border: 1px solid #bd362f;
      }

      .btn-danger:hover {
        color: #fff;
        background-color: #bd362f;
      }

      .btn:focus {
        outline: none;
      }

      .todo-container {
        width: 600px;
        margin: 0 auto;
      }
      .todo-container .todo-wrap {
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 5px;
      }






</style>
