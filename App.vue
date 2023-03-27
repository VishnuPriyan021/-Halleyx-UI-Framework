<template>
  <img src="./assets/logo.png">
  <div>
    <p>
      If halley kit is successfully added to this project, you'll see an
      <code v-text="'<hlx-button>'"></code>
      below
    </p>
    <hlx-button class="primary">el-button</hlx-button>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
