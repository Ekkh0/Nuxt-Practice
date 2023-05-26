<template>
  <div class="text-xs">
    <div class="background">
      <img :src="require('@/assets/1.jpg')" alt="">
    </div>
    <form class="formcontainer" ref="loginform" @submit.prevent="login">
      <div action="" class="form">
      <div><h1>Login</h1></div>
      <label class="label" for="">Email</label>
      <input class="inputtext" type="text" name="" id="" placeholder="Email">
      <label class="label" for="">Password</label>
      <input class="inputtext" type="text" name="" id="" placeholder="Password">
      <div class="btncont">
        <router-link to="/regist" tag="button">Register</router-link>
        <h4>OR</h4>
        <button class="login" type="submit
        ">Login</button>
      </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  mounted(){
    this.$axios.$get('/sanctum/csrf-cookie')
  },
  methods:{
   async login(){
    try{
      const formData = new FormData(this.$refs.loginform);
      console.log('Terjalan!');
      console.log(formData);
      await this.$auth.loginWith('laravelSanctum', {data: formData});

      this.$router.push({
        path:'/regist',
      })
    }catch(err){
      // console.log(err);
    }
   }
  }
}
</script>
