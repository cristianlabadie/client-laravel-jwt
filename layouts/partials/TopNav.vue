<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="success">
      <div class="container">
        <nuxt-link class="navbar-brand" to="/">Nuxt Client</nuxt-link>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/dashboard">Dashboard</nuxt-link>
            </li>
          </b-navbar-nav>
          <b-navbar-nav class="ml-auto">
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/login">Login</nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/auth/register">Register</nuxt-link>
            </li>
          </b-navbar-nav>

        </b-collapse>
      </div>
    </b-navbar>
  </div>
</template>
<script>
export default {
  name: "",
  data: () => ({

  })
}
</script>
<style lang="scss" scoped>
</style>
