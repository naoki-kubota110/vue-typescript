<template>
  <div id="app">
    <h1>Vue / Typescript Todo</h1>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>コメント</th>
          <th>状態</th>
          <th>-</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(todo,index) in todos" :key="index">
          <th>{{todo.id}}</th>
          <td>{{todo.title}}</td>
          <td>
            <button @click="changeStatus(index)">
              {{todo.status? "完了":"作業中"}}
            </button>
          </td>
          <td>
            <button @click="deleteTodo(index)">
              削除
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <h2>新しい作業の追加</h2>
      <input type="text" v-model="inputText">
      <button @click="addTodo">追加</button>
      <p>{{errorMsg}}</p>
      <Form @addtask="mozi = $event"></Form>
      {{mozi}}
  </div>
</template>

<script lang="ts">
import { Component, Vue ,Watch, Prop} from 'vue-property-decorator';
import Form from './components/Form.vue'
import {TodoItem} from './todo'


@Component({
  components: {
    Form
  },
})
export default class App extends Vue {
  inputText: string = ""
  errorMsg :string = ""
  todos :TodoItem[]= []
  nextId:number= 0
  status:boolean = false
  Todostatus:string = ""
  mozi:string = ""
  private addTodo(){
    const task = this.inputText
    if(task === ""){
      alert("入力してください")
    }else if(this.errorMsg !==""){
     alert("10文字以内で入力してください")
    }else{
        this.todos.push({
        id:this.nextId += 1,
        title: task,
        status: false
      })
      this.inputText = ""
    }
  }
  
  private deleteTodo(index){
    this.todos.splice(index,1)
  }

  private changeStatus(index){
    this.todos[index].status = !this.todos[index].status
  }

  @Watch("inputText")
   public num(){
     if(this.inputText.length > 10){
       this.errorMsg = "10文字以内で入力してください"
     }else{
       this.errorMsg = ""
     }
   }



}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
