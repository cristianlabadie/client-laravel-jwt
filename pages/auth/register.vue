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
          <h3>Registro</h3>
        </div>
        <div class="card-body">
          <form @submit.prevent="registro" class="" action="index.html" method="post">
            <div class="form-group">
              <label>Nombre</label>
              <input type="text" class="form-control" :class="{'is-invalid': errors.name}" placeholder="nombre..." v-model="form.name">
              <div class="invalid-feedback" v-if="errors.name">
                {{errors.name[0]}}
              </div>
            </div>
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
              <input type="submit" name="" value="Registrar" class="btn btn-primary w-100">
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
                name: '',
                email: '',
                password: ''
            },
            error: this.$route.query.error
        }
  },
  methods: {
    async registro(){
      try {
        await this.$axios.post('/auth/register', this.form);
      } catch (e) {
        return ;
      }
      this.$auth.login({data: this.form});

      this.$router.push({name: 'index'});
    }
  }
}
</script>
<style lang="scss" scoped>
</style>
