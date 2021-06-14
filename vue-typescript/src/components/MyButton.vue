<template>
  <button @click="onClick">MyButton</button>
</template>

<script lang="ts">
  import {Component, Vue,Prop, Emit} from "vue-property-decorator";


//@マークで始まる単語はアノテーション
  @Component
  export default class MyButton extends Vue{
    private count: number = 0
    @Prop()
    public greet?:string

    @Emit()
    public click(){
      console.log("my button click")
    }
    public onClick(){
      alert(this.greet)
      this.click()
      this.count ++
      this.click(this.count)
      console.log("mybuton onclick")
    }
  }
</script>