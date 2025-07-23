<template>
  <div>
    <!--Text binding-->
    {{ welcome_msg }}
    {{ number }}
  </div>
  <!--click on parent but increment through child-->
  <button @click=handleClick>Click me
    <HelloWorld ref="childRef" :number="number" @update:number="number=$event"></HelloWorld>
  </button>
 <!--emit concepts-->
 <HelloWorld @custom-event="handleCustomEvent"></HelloWorld>
 <!--v-model-->
 <input type="text" v-model="user.name" />
 <input type="email" v-model="user.email"/>
 <button @click="handleUser">Click me to check user information</button>
 <div v-if="isinfo">
  <p>User Information</p>
  name:{{ user.name }}
  email:{{ user.email }}
 </div>
</template>

<script>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import { reactive } from 'vue';
import { provide } from 'vue';
export default {
  // Options API
  data() {
    return {
      welcome_msg: "Welcome to the vue.js"
    };
  },
  components:{HelloWorld},
  methods:{
  handleCustomEvent(payload){
    console.log("HI,I am",payload)
  },
  handleClick(){
    this.$refs.childRef.increment();
  },
  },
  // Composition API
  setup() {
    const isinfo=ref(false)
    const user=reactive({user:"",email:""})//reactive make a object reactive
    const number = ref(0); // ref makes a variable reactive. When its value changes, Vue notices it and updates the DOM automatically..
    const handleUser=()=>{
    if(user.name && user.email){
      isinfo.value=true;
    }
  }

  provide("appname","HI Whatsapp")//Pass data from parent to a deep child without uisng props.
    return {
      number,
      user,
      isinfo ,// must return to use in template
      handleUser
    };
  }
};
</script>
