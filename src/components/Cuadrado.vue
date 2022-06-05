<template>

  <section class="src-componentes-Cuadrado">
   
      
      <div id="container">
        <div class="square"></div>
        <div class="square"></div>
        <div class="square"></div>
        <div class="square"></div>
        <div class="square"></div>
        <div class="square"></div>
      </div>

  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-componentes-Cuadrado',
    props: [],
    mounted () {   
    },
    data () {
      return {
        squares:  document.querySelectorAll(".square")
      }
    },
    methods: {
    },
    computed: {
    }
}


</script>

<style scoped lang="css">

  .square {
        width: 30%;
        background: blue;
        padding-bottom: 30%;
        float: left;
        margin: 1.66%;
        border-radius: 10%;
        transition: background 0.8s;
        -webkit-transition: background 0.8s;
        -moz-transition: background 0.8s;
    }

    #container {
        margin: 20px auto;
        max-width: 600px;
    }

</style>
