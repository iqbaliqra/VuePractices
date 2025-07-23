<script>
import { inject } from 'vue';


export default {
  name:"HelloWorld",
  props:['number'],
  methods: {
    increment(){
      this.$emit('update:number',this.number+1)
    },
    sendToParent(){
      this.$emit('custom-event',"IQ") //emits contains function name and payload
    }
  },
  setup(){
    const appname=inject("appname")
    return{
      appname
    }
  }
}
</script>

<template>
  <div v-if="!number && number!==0">
  <button @click="sendToParent">Send Event to the parent</button>
   <p>Injected Name: {{ appname }}</p>
</div>
</template>