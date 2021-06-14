<template>
    <button @click="onClick">Reset</button>
</template>

<script lang="ts">
    import {Component, Emit, Prop, Vue} from "vue-property-decorator";

    @Component
    export default class ResetButton extends Vue {
        @Prop()
        public initialValue!: string;

        /** モデルバインドのために記述必須 */
        @Prop()
        public value!: string;

        public created(){
          this.initialValue = this.value
        }

        /** モデルバインドのために記述必須 */
        @Emit()
        public input(value: string) {
          console.log("resetEimit")
        }

        public onClick(){
            this.input(this.initialValue);
            console.log("reset")
        }
    }
</script>