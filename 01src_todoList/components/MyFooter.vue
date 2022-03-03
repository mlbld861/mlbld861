<template>
  <div class="todo-footer" v-show="total">
    <label>
      <input type="checkbox" :checked="isAll" @change="checkAll"/>
    </label>
    <span>
          <span>已完成{{doneTotal}}</span> / 全部 {{total}}
        </span>
    <button class="btn btn-danger" @click="clearAllTodo">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props:['todos','checkAllTodo','clearTodos'],
  computed:{
    total(){
      return this.todos.length
    },
    doneTotal(){
      // return this.todos.filter(todo=>todo.done==true).length
      return this.todos.reduce((pre,current)=>{
        return pre+(current.done ? 1 : 0)
      },0)
      // 第一个参数是函数，第二个参数是0，current是每一个头都项
    },
    isAll(){
      return this.total===this.doneTotal
    },
  },
  methods:{
    checkAll(e){
      this.checkAllTodo(e.target.checked)
    },
    clearAllTodo(){
      this.clearTodos()
    }
  }

}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>