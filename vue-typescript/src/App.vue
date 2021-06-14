<template>
  <div id="app">
    <h1>Vue / Typescript</h1>
    <p>{{greetText}}</p>
    <p>{{count}}</p>
    <p v-if="isRegular">thanks</p>
    <MyButton  :greet="greetText" @click="clickEmit"></MyButton>
    <ResetButton initialValue="hello" v-model="greetText"></ResetButton>
  </div>
</template>

<script lang="ts">
import { Component, Vue ,Watch} from 'vue-property-decorator';
import MyButton from "./components/MyButton.vue"
import ResetButton from "./components/ResetButton.vue"

@Component({
  components: {
    MyButton,
    ResetButton
  },
})
export default class App extends Vue {
  private count: number = 0
    public greetText:string = "こんにちは"
    private isRegular: boolean = false

  public clickEmit(count: number){
    console.log("app click")
    this.count = count
    if(this.count > 5){
      this.isRegular= true
    }
    this.greetText = "haaiiiiiiiiiiiiiiiii"
  }
  @Watch("count")
  public countChange(){
    if(this.count === 5){
      alert("zyourenn")
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
