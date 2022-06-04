<template>
  <section class="src-components-navbar">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <div class="collapse navbar-collapse navigator" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <button href="#">News Colors </button>
                </li>
                <li class="nav-item active">
                    <button  href="#">Easy</button>
                </li>
                <li class="nav-item active selected">
                    <button href="#" @click="easyButton">Hard</button>
                </li>
                </ul>
            </div>
        </nav>
    </section>
</template>

<script lang="js">
  export default  {
    name: 'src-components-navbar',
    props: [],
    mounted () {
    },
    data () {
      return {
        colorCount: 6,
        isHard: true,
        colors: [],
        //squares: document.querySelectorAll(".square"),
        //colorDisplay: document.getElementById("colorDisplay"),
        //messageDisplay: document.getElementById("message"),
        //pickedColor: colors[PickColor()],
        //h1: document.querySelector("h1"),
        //restartButton: document.querySelector("#reset"),
        //header: document.querySelector("#header"),
        //easyButton: document.querySelector("#easy"),
        //hardButton: document.querySelector("#hard")*/
      }
    },

    methods: {
      easyButton(){
        if (isHard) {
            isHard = false;
            easyButton.classList.add("selected");
            hardButton.classList.remove("selected");
            colorCount = 3;
            for (var i = 0; i < colorCount; i++) {
                squares[(i+3)].style.display = "none";
        }
        }
           restart();
       },

         hardButton(){
            if (!isHard) {
                isHard = true;
                hardButton.classList.add("selected");
                easyButton.classList.remove("selected");
                colorCount = 6;
                restart();
                for (var i = 3; i < 6; i++) {
                    squares[i].style.display = "block";
                }
            }
        },
    },


    restartButton(){
	    //restart();
    },

    init(){
       /* for (var i = 0; i <squares.length; i++) {
            console.log(colors[i])
           //squares[i].style.backgroundColor = colors[i];
            //squares[i].addEventListener("click", function(){
            var clickedColor = this.style.backgroundColor;
		if (clickedColor === pickedColor) {
			//.textContent = "You Picked Right!";
			setAllColorsTo(pickedColor);
			restartButton.textContent = "Play Again!";
			//header.style.backgroundColor = pickedColor;
		} else {
			this.style.backgroundColor = "#232323";
			//messageDisplay.textContent = "Try Again!";
			//messageDisplay.style.color = "#000000";
		}*/
        
    },
    
    //setAllColorsTo(color) {
       /* squares.forEach(function (square){
            square.style.backgroundColor = color;
        })*/
    //},

    PickColor(){
        //var quantity;
      /*  if (isHard) {
            quantity = 6;
        } else {
            quantity = 3;
        }
        return Math.floor(Math.random() * quantity );*/
    },


    restart(){
        colors = createNewColors(colorCount);
        pickedColor = colors[PickColor()];
        colorDisplay.textContent = pickedColor;
        this.textContent = "Pick New Colors!";
        header.style.backgroundColor = "steelblue";
        messageDisplay.textContent = "";
        restartButton.textContent = "New Colors!";
        for (var i = 0; i <squares.length; i++) {
            squares[i].style.backgroundColor = colors[i];
        }
    }
}  
    computed: {

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
    }

     .selected {
        background-color: steelblue;
        color: white;
    }

   /* h1 {
        font-weight: normal;
        line-height: 1.1;
        padding: 20px 0;

    }*/

    
   /*#colorDisplay {
        font-size: 200%;
    }*/

/*
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
    */
</style>


