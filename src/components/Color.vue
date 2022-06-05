<template>
  <div class="hello">
    	<div class="header" id="header">
        <h1>The Great 
          <br>
          <span id="colorDisplay">RGB</span>
          <br>
            Guessing Game</h1>
    </div> 
    <Navbar :header="header" @header="header=$event" />   
  </div>
</template>

<script>

import Navbar from './Navbar.vue'

export default {
  name: 'Color',
  components : {
    Navbar
  },
  props: [],
  mounted () {
  },
  data () {
    return {
      colorDisplay: document.getElementById("colorDisplay"),
      header:  document.getElementById("header"),
    }
  },
  methods: {
  }
}
</script>

<style scoped lang="css">

.header {
      transition: all 0.3s;
      text-transform: uppercase;
      background: steelblue;
      text-align: center;
      margin: 0;
      color: white;  
}

#colorDisplay {
      font-size: 150%;
}

</style>
