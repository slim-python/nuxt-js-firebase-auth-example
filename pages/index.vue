
<template>
  <div>
    <button class="text-6xl text-center font-bold p-8" >Create a new account </button>
    <NuxtLink to="/login" class="bg-gray-200">login page</NuxtLink>

    <div class="bg-gray-200 p-8">
      <div>
        <form @submit.prevent="login" class="p-2 m-2 flex flex-col">
          <h2 class="my-4 mx-4 w-1/3 p-4 text-2xl"> Register an account</h2>
          <input class="my-4 mx-4 w-1/3 p-4" type="email" placeholder="Email address..." v-model="email" /> 
          <input class="my-4 mx-4 w-1/3 p-4" type="password" placeholder="password..." v-model="password" /> 
          <button type="button" class="my-4 mx-4 w-1/3 p-4 bg-indigo-400 " @click="createUser">Register</button>
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
    async createUser() {
      console.log("strted")
      try {
        await this.$fire.auth.createUserWithEmailAndPassword(
          this.email,
          this.password
        )
        this.$router.push('/aftersignup')
      } catch (e) {
        handleError(e)
      }
    }
  }
}
</script>

