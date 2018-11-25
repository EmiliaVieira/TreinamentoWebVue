<template>
  <div class="absolute-center">
    <login-form @logged="saveUser"></login-form>
  </div>
</template>

<script>
import LoginForm from '../components/Login.vue'
import { LocalStorage } from 'quasar'
export default {
  components: {
    'login-form': LoginForm
  },
  name: 'Login',
  methods: {
    saveUser: function (resp) {
      console.log('Salvar usuario logado')
      LocalStorage.set('user', resp)
    }
  }
}
</script>

<style>
</style>
