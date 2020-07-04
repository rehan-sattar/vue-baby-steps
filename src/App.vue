<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "./layout/Header";

export default {
  name: "app",
  components: {
    Header
  }
};
</script>

<style>
</style>
