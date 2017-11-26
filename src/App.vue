<template>
    <div>
        <login @registered="register" v-show="!enter_register"></login>
        <register @unregister="unregister" v-show="enter_register"></register>
    </div>
</template>

<script>
    import Login from './Login.vue';
    import Register from './components/Register.vue';
  export default {
    components:{
        Login,
        Register
    },
      methods: {
          register(){

              console.log("Called from parent");
              this.enter_register =  true;
          },
          unregister(){
              this.enter_register = false;
          }
      },
    data () {

      return {
            enter_register: false
      }
    }
  }
</script>
