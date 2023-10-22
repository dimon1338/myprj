<template>
  <div class="container">
    <NavComp></NavComp>
    <router-view></router-view>
  </div>
</template>

<script>
import NavComp from './components/Navigation.vue';

export default {
  name: 'App',
  components: {
    NavComp,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.container {
  background-color: #dfff4f;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
}
</style>
