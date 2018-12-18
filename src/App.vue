<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/4.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <!--<newElement v-bind:va="message" msg="Just test header" />-->
    <ProductApp/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
/*import newElement from './components/newElement'*/
import ProductApp from './components/ProductApp.vue'

export default {
  name: 'app',
  components: {
    ProductApp,
    HelloWorld,
  },
  /*data: () => {
    return {
      message: "new header"
    }
  }*/


}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
