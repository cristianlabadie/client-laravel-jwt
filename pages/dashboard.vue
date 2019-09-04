<template>
  <div class="container">
    <h1>Welcome to the dashboard {{ user.name}}</h1>
  </div>
</template>
<script>
export default {
  name: "",
  data: () => ({

  }),
  middleware: 'auth'
}
</script>
<style lang="scss" scoped>
</style>
