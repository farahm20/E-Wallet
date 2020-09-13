<template>
  <div id="app">
    <home-Top></home-Top>
    <router-view></router-view>
  </div>
</template>

<script>
import Top from './components/Top';

export default {
  name: 'App',
  data() {
    return {
    }
  },
  components: {
    'home-Top':Top,
  },
}
</script>

<style>

</style>