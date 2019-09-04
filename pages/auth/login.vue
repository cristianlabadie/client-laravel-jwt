<template>
  <div class="container">
    <div class="col-md-6 offset-md-3">
      <div v-if="error" class="alert alert-danger mb-2" role="alert">
        Tu token parece invalido, intentalo de nuevo.
      </div>
      <div class="card mt-4">
        <div class="card-header">
          <SocialLogin />
          <hr>
          <h3>Iniciar Sesión</h3>
        </div>
        <div class="card-body">
          <form @submit.prevent="login" class="" action="index.html" method="post">
            <div class="form-group">
              <label>Email</label>
              <input type="email" class="form-control" :class="{'is-invalid': errors.email}" placeholder="email..." v-model="form.email">
              <div class="invalid-feedback" v-if="errors.email">
                {{errors.email[0]}}
              </div>
            </div>
            <div class="form-group">
              <label>Contraseña</label>
              <input type="password" class="form-control" :class="{'is-invalid': errors.password}" placeholder="contraseña..." v-model="form.password">
              <div class="invalid-feedback" v-if="errors.password">
                {{errors.password[0]}}
              </div>
            </div>
            <div class="form-group">
              <input type="submit" name="" value="Ingresar" class="btn btn-primary w-100">
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import SocialLogin from '@/components/SocialLogin'
export default {
  components: {
    SocialLogin
  },
  middleware: 'guest',
  name: "",
  data() {
        return {
            form: {
                email: '',
                password: ''
            },
            error: this.$route.query.error
        }
  },
  methods: {
    async login(){
      try {
        await this.$auth.login({data: this.form});
      } catch (e) {
        return ;
      }


      this.$router.push(this.$route.query.redirect ? this.$route.query.redirect : '/');
    }
  }
}
</script>
<style lang="scss" scoped>
</style>
