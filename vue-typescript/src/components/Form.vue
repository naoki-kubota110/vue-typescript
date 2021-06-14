<template>
<div>
  <input v-model="input">
  <div>
  <button @click="addTask()">add</button>
  </div>
</div>
</template>

<script lang="ts">
import {Component, Vue,Prop, Emit} from "vue-property-decorator";

@Component
export default class Form extends Vue{
  input :string=""
  @Emit()
  addTask(){
    console.log("hello")
    this.$emit("addtask",this.input)
    this.input = ""
  }
}

</script>