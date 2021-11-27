
<template>
  <div>
    <button class="text-6xl text-center font-bold p-8" >Login here</button>
    <NuxtLink to="/" class="bg-gray-200">SIGNUP page</NuxtLink>
    <div class="bg-gray-200 p-8">
      <div>
        <form @submit.prevent="login" class="p-2 m-2 flex flex-col">
          <h2 class="my-4 mx-4 w-1/3 p-4 text-2xl"> Login in with your email and password</h2>
          <input class="my-4 mx-4 w-1/3 p-4" type="email" placeholder="Email address..." v-model="email" /> 
          <input class="my-4 mx-4 w-1/3 p-4" type="password" placeholder="password..." v-model="password" /> 
          <button type="button" class="my-4 mx-4 w-1/3 p-4 bg-indigo-400 " @click="loginUser">Register</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
// import firebase from '@nuxtjs/firebase'


export default {
  data: () => ({
    email: "",
    password: ""
  }),
  methods: {
    async loginUser() {
      console.log("strted")
      try {
        await this.$fire.auth.signInWithEmailAndPassword(
          this.email,
          this.password
        )
        this.$router.push('/afterlogin')
      } catch (e) {
        handleError(e)
      }
    }
  }
}
</script>

