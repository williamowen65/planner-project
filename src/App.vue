<template>
  <Navbar/>
  <router-view/>
</template>

<script>
import Navbar from './components/Navbar'

export default {
  components: { Navbar },
  data() {
    return {

    }
  }
  
}

</script>

<style>
body {
  background: #f2f2f2;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  max-width: 600px;
  margin: 0 auto;
  color: #555;
}

</style>
