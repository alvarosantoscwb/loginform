<template>
  <img src="~assets/wave.png" class="wave" alt="login-wave">
  <div class ="row" style="height: 90vh">
    <div class="col-0 col-md-6 flex justify-center content-center">
      <img src="~assets/login.svg" class="responsive" alt="login-image">
  </div>
 <div v-bind:class="{'justify-center': $q.screen.md || $q.screen.sm || $q.screen.xs}" class="col-12 col-md-6 flex content-center">
   <q-card v-bind:style="$q.screen.lt.sm ? {'width': '80%'} : {'width': '50%'}">
     <q-card-section>
       <q-avatar size="103px" class="absolute-center shadow-10">
         <img src="~assets/avatar.svg" alt="avatar">
        </q-avatar>
     </q-card-section>
      <div class="q-pt-lg">
        <div class="col text-h6 ellipsis flex justify-center">
          <h2 class="text-h2 text-uppercase q-my-none text-weight-regular"></h2>
          </div>
          </div>
          <q-card-section>
            <q-form class="q-gutter-md" @submit.prevent="submitForm">
            <q-input label="Username" v-model="login.username">
            </q-input>
            <q-input label="Password" type="password" v-model="login.password">
            </q-input>
            <q-btn class="full-width" color="primary" label="Login" type="submit" rounded></q-btn>
            <div class="text-center q-mt-sm q-gutter-lg">
              <router-link class="text-white" to="/login">Forgot your password?</router-link>
              <router-link class="text-white" to="/">Create an account</router-link>
            </div>
            </q-form>
          </q-card-section>
        </q-card>
      </div>
    </div>
</template>

<script>
import { useQuasar } from 'quasar'
let $q
export default {
  name: 'Login',
  data () {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    SubmitForm () {
      if (!this.login.username || !this.login.password) {
        $q.notify({
          type: 'negative',
          message: 'Incorrect password. Please try again or click "Forgot password?" to choose another.'
        })
      } else if (this.login.password.length < 6) {
        $q.notify({
          type: 'negative',
          message: 'password must be 6 characters or more.'
        })
      } else {
        console.log('login')
      }
    }
  },
  mounted () {
    $q = useQuasar()
  }
}

</script>

<style scoped>

.wave {
  position: fixed;
  height: 100%;
  left: 0;
  bottom: 0;
  z-index: -1;
}

</style>
