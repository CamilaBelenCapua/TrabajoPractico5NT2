<template>
  <section class="src-components-navbar">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <div class="collapse navbar-collapse navigator" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <button href="#" id="reset" @click="restartButtonFun">News Colors </button>     
                </li>
                <span id="mensaje"> </span>
                <li class="nav-item active">
                    <button  href="#" id="easy" class="selected" @click="easyButtonFunc">Easy</button>
                </li>
                <li class="nav-item active selected">
                    <button href="#" id="hard" class="selected" @click="hardButtonFunc">Hard</button>
                </li>
                </ul>
                
            </div>
        </nav>
    </section>
</template>

<script lang="js">
import Cuadrado from './Cuadrado.vue'
import Color from './Color.vue'

  export default  {
    name: 'src-components-navbar',
    components : {
        Cuadrado,
        Color
    },
    props: ['header'],

    mounted () {
        this.colorDisplay = Color.data().colorDisplay,
        this.squares = Cuadrado.data().squares,
        this.messageDisplay = document.querySelector("#mensaje")
        this.easyButton = document.querySelector("#easy"),
        this.hardButton = document.querySelector("#hard"),
        this.restartButton = document.querySelector("#reset"),
        this.colors = this.createNewColors(this.colorCount);
        this.pickedColor = this.colors[this.PickColor()]
        this.colorDisplay.textContent = this.pickedColor;
        
        for (var i = 0; i <this.squares.length; i++) {
            this.squares[i].style.backgroundColor = this.colors[i]
            this.squares[i].addEventListener("click", event => {
                var square = event.path[0]
                var clickedColor = square.style.backgroundColor;
                
                if (clickedColor === this.pickedColor) {
                    this.messageDisplay.textContent = "You Picked Right!";
                    this.setAllColorsTo(this.pickedColor);
                    this.restartButton.textContent = "Play Again!";
                    header.style.backgroundColor = this.pickedColor;
                } else {
                    square.style.backgroundColor = "#FFFFFF";
                    this.messageDisplay.textContent = "Try Again!";
                    this.messageDisplay.style.color = "#000000";
                }
            });
       }
        
    },

    data () {
      return {
        colorCount: 6,
        isHard: true,
        colors: [],
        squares: null,
        messageDisplay: null,
        colorDisplay: null,
        pickedColor: null,
        restartButton: null,
        easyButton: null,
        hardButton: null
      }
    },

    methods: {
      easyButtonFunc(){
        if (this.isHard) {
            this.isHard = false;
            this.easyButton.classList.add("selected");
            this.hardButton.classList.remove("selected");
            this.colorCount = 3;
            for (var i = 0; i < this.colorCount; i++) {
                this.squares[(i+3)].style.display = "none";
            }
        }
           this.restart();
       },

      hardButtonFunc(){
        if (!this.isHard) {
            this.isHard = true;
            this.hardButton.classList.add("selected");
            this.easyButton.classList.remove("selected");
            this.colorCount = 6;
            this.restart();
            for (var i = 3; i < 6; i++) {
                this.squares[i].style.display = "block";
            }
        }
    },

    restartButtonFun(){
	    this.restart();
    },

    setAllColorsTo(color) {
       this.squares.forEach(function (square){
            square.style.backgroundColor = color;
        })
    },

    PickColor(){
        var quantity;
        if (this.isHard) {
            quantity = 6;
        } else {
            quantity = 3;
        }
        return Math.floor(Math.random() * quantity );
    },


    restart(){
        console.log('Entro al restart')
        this.colors = this.createNewColors(this.colorCount);
        this.pickedColor = this.colors[this.PickColor()];
        this.colorDisplay.textContent = this.pickedColor;
        this.textContent = "Pick New Colors!";
        header.style.backgroundColor = "steelblue";
        this.messageDisplay.textContent = "";
        this.restartButton.textContent = "New Colors!";
     
        for (var i = 0; i <this.squares.length; i++) {
            this.squares[i].style.backgroundColor = this.colors[i];
        }
       
    },

    createNewColors(numbers){
        var arr = [];
        for (var i = 0; i < numbers; i++) {
            arr.push(this.createRandomStringColor());
        }
        return arr;
    },

    createRandomStringColor(){
        var newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
        return newColor;
    },

    randomInt(){
        return Math.floor(Math.random() * 256);
    }
},  
    computed: {

    }
}    

</script>
<style scoped lang="css">

   .message {
        color: steelblue;
        display: inline-block;
        width: 20%;
    }

    button {
        border: none;
        background-color: white;
        font-family: "Montserrat", "Avenir";
        text-transform: uppercase;
        height: 100%;
        font-weight: 700;
        letter-spacing: 1px;
        color: steelblue;
        transition: all 0.3s;
        outline: none;
    }

    button:hover {
        color: white;
        background-color: steelblue;
    }

    .navigator {
        background: #ffffff;
        height: 30px;
        text-align: center;
        margin: 0;
        margin-top: -12px;
        padding-top: 10px;
        margin-left: 350px;
    }

    .selected {
        background-color: steelblue;
        color: white;
    }

</style>


