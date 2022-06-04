<template>
  <div class="hello">
    	<div class="header">
        <h1>The Great 
          <br>
          <span>RGB</span>
          <br>
            Guessing Game</h1>
    </div>    
  </div>
</template>

<script>
export default {
  name: 'Color',
  props: [],
  mounted () {
  },
  data () {
    return {
  }
  },

  methods: {
     createNewColors(numbers){
        var arr = [];
        for (var i = 0; i < numbers; i++) {
            arr.push(createRandomStringColor());
        }
        return arr;
    },

    createRandomStringColor(){
        var newColor = "rgb(" + randomInt() + ", " + randomInt() + ", " + randomInt() + ")" ;
        return newColor;
    },

    randomInt(){
        return Math.floor(Math.random() * 256);
    }
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

.colorDisplay {
      font-size: 200%;
}
</style>
