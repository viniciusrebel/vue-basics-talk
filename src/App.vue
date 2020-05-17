<template>
  <div id="app">
    <section class="app-header">
      <img 
        alt="Vue logo"
        src="./assets/logo.png"
      >
      <h1>Vue Basics</h1>
    </section>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

.app-header{
  display: flex;
  align-items: center;
  margin-bottom: 12px;
  border-bottom: 1px solid #dbdbdb;
}
.app-header img {
    height: 30px;
    margin-right: 16px;
  }
.app-header h1 {
  margin: 0;
}
</style>
