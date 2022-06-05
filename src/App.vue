<template>
  <div class="container-fluid mt-3">
    <div>
      <Color/>
	    <!--<Navbar/>-->
	    <Cuadrado/>
    </div> 
  </div>
</template>

<script>

import Color from './components/Color.vue'
import Navbar from './components/Navbar.vue'
import Cuadrado from './components/Cuadrado.vue'


export default {
  name: 'App',
  components: {
    Color,
    Navbar,
    Cuadrado
  }
}
</script>


<style scoped lang="css">

</style>
