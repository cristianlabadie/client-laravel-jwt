<template>
  <div class="container">
    <div class="col-md-6 offset-md-3">
      <div class="card mt-4">
        <div class="card-header">
          <h3>Registro</h3>
        </div>
        <div class="card-body">
          <form @submit.prevent="registro" class="" action="index.html" method="post">
            <div class="form-group">
              <label>Nombre</label>
              <input type="text" class="form-control" placeholder="nombre..." v-model="form.name">
            </div>
            <div class="form-group">
              <label>Email</label>
              <input type="email" class="form-control" placeholder="email..." v-model="form.email">
            </div>
            <div class="form-group">
              <label>Contraseña</label>
              <input type="password" class="form-control" placeholder="contraseña..." v-model="form.password">
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
export default {
  name: "",
  data: () => ({
    form:{
      name: '',
      email: '',
      password: ''
    }
  }),
  methods: {
    async registro(){
      await this.$axios.post('/auth/register', this.form);

      this.$auth.login({data: this.form});

      this.$router.push({name: 'index'});
    }
  }
}
</script>
<style lang="scss" scoped>
</style>
