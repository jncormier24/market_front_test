<template>
  <section class="container mx-auto flex flex-col justify-center items-center h-screen">
    <message :message="message" v-if="message" />
    <div class="flex flex-col w-1/3 shadow rounded border px-3 py-2">
      <form method="post" @submit.prevent="login">
        <div class="flex flex-row justify-between items-center mb-2">
          <label for="email"
            class="font-md uppercase text-grey-darkest w-32">Email</label>
          <input type="email" 
            class="shadow-inset px-3 py-2 rounded border appearance-none"
            v-model="email" 
            required>
        </div>
        <div class="flex flex-row justify-between items-center mb-2">
          <label for="password"
            class="font-md uppercase text-grey-darkest w-32">Password</label>
          <input type="password" 
            class="shadow-inset px-3 py-2 rounded border appearance-none"
            v-model="password" 
            required>
        </div>
        <button 
          @click="login"
          class="bg-blue-lighter text-blue-darkest rounded-full border-blue-darkest px-3 py-2 mb-2">
          Login
        </button>
      </form>
    </div>
  </section>
</template>

<script>
import message from '~/components/message'
export default {
  components: {
    message
  },
  data() {
    return {
      email: '',
      password: '',
      message: null
    }
  },
  methods: {
    async login() {
      try {
        await this.$auth.loginWith('api', {
          data: {
            email: this.email,
            password: this.password
          }
        })

        this.$router.push('/')
      } catch (e) {
        this.message = e
      }
    }
  }
}
</script>
