<template>
  <div id="app">
    <v-home></v-home>
  </div>
</template>

<script>
import homes from './components/home'
export default {
  name: 'app',
  components:{
    'v-home':homes//组件名是 import 后的组件名
  }
}
</script>

<style>
</style>
