<template>
  <q-card color="dark" class="q-pa-lg">
    <q-card-title>
      <div class="row justify-center items-center">
        <div class="col-md-6 text-center">
          <img src="../statics/logo.png" width="50%"/>
        </div>
        <div id="login-title" class="col-md-6">
          <p class="text-center">
            Treinamento Web
          </p>
          <p class="text-center">
            VueJs + Quasar
          </p>
        </div>
      </div>
    </q-card-title>
    <q-card-separator></q-card-separator>
    <q-card-main>
      <q-field
        dark
        icon="fas fa-user"
        :helper="capitalize($t('label.userhelper'))"
        >
        <q-input color="primary" dark suffix="@landix.com.br" v-model="username"/>
      </q-field>
      <q-field
        dark
        icon="fas fa-key"
        :helper="capitalize($t('label.passwordhelper'))"
        >
        <q-input type="password" max-length="20" color="primary" dark v-model="password"/>
      </q-field>
      <div class="text-right">
      <q-btn
        color="secondary"
        @click="login"
        label="Entrar"
        icon="done"
      />
      </div>

    </q-card-main>
  </q-card>
</template>

<script>
import { format } from 'quasar'
const { capitalize } = format
export default {
  name: 'Login',
  data () {
    return {
      username: undefined,
      password: undefined,
      capitalize
    }
  },
  computed: {
    fullUserName: function () { return this.username ? this.username + '@landix.com.br' : undefined }
  },
  methods: {
    login () {
      this.$axios.post('/landix/login/', {username: this.fullUserName, password: this.password})
        .then((response) => {
          this.$emit('logged', response.data)
        })
        .catch(() => {
          alert('Erro no loggin')
        })
    }
  }
}
</script>

<style>
</style>
