<template>
  <div id="app">
    <home></home>
  </div>
</template>

<script>
import Home from './components/Home'
import Itunes from '@/components/Itunes'
import Mytunes from '@/components/Mytunes'
export default {
  name: 'app',
  components: {
    Home,
    Itunes,
    Mytunes
  }
}
</script>

<style>
#app{
  height: 100vh;
  width: 100vw;
 
}
</style>
