<template>
    <div class="mainsection">
        <div class="main-image1">
            <div class="image1">
           <div class="text1"> <u>This is a page for<br> potato voting.</u></div>
                </div>
                <div class="image2">
                     <div class="text2">Made by with love by[name].</div>
                    </div> 
</div>

<div class="main-image2">
<div class="dish-image1">
    <div class="dish1">
        <img src="https://raw.githubusercontent.com/cognitedata/fe-interview-challenge-vue/master/resources/mashedPotato.jpg" alt="food" height="72" width="72">
     </div>
<div class="button1">
   <input type="button" value="Like"  @click="likes+=1"/>
   </div>
<div class="btn1">
<p style="color:blue"> like:{{likes}}</p>
</div>
</div>
<div class="dish-image2">
    <div class="dish2">
        <img src="https://raw.githubusercontent.com/cognitedata/fe-interview-challenge-vue/master/resources/bakedPotato.jpeg" alt="food" height="72" width="72">
</div>
<div class="button2">
<input type="button" value="Dislikes" @click="Dislikes+=1"/>
</div>
<div class="btn2">
<p style="color:white">Dislikes:{{Dislikes}}</p>
</div>
</div>
<div class="dish-image3">
<div class="button3">
<input type="button" value="Reset"  @click="Reset" />
</div>
<div class="btn3">
<p style="color:white">Total clicks:{{likes+Dislikes}}</p>
</div>
</div>   
      </div>
      </div>
</template>
<script>
export default {
    name:"foodmenu",
    data(){
        return{
likes:0,
Dislikes:0
        }
    },
    methods:{
Reset(){
 this.likes=0,this.Dislikes=0;
} 
    }
    }
</script>
<style scoped>
.main-image1{
    width:100%;
    display: flex;
    height:400px;
}
.image1{
     width:48%;
     background-color: blue;
      position: absolute;
height: 400px;
}
.text1{
     font-size: 49px;
      margin-top: 70px;
    text-align: center;
    position: relative;
    top: 90px;
    }
.image2{
    width:140%;
margin-left:50%;
 background-repeat: no-repeat;
background-image: url("https://raw.githubusercontent.com/cognitedata/fe-interview-challenge-vue/master/resources/thumbs.png")
}
.text2{
     font-size: 30px;
      margin-left: 70px;
    text-align: center;
    position: relative;
    top:170px;
}
.main-image2{
    background-color: black;
}
.dish-image1{
display: flex;
}
.dish1{
    text-align: center;
    margin-top:3%;
      margin-left: 40%;
   }
 .button1{
      margin-left:2%;
    text-align: center;
    position: relative;
    top:70px;
    border: none;
    }
    .button1 input{
    background-color: green;
    border-color: black;
}
    .btn1{
        margin-left:2%;
          position: relative;
    top:60px;
    }
.dish-image2{
display: flex;
  }
.dish2{
    text-align: center;
    margin-top:1%;
      margin-left: 40%;
   }
 .button2{
      margin-left:2%;
    text-align: center;
    position: relative;
    top:40px;
}
.button2 input{
    background-color: red;
      border-color: black;
}
 .btn2{
        margin-left:2%;
          position: relative;
    top:30px;
    }
.dish-image3{
display: flex;
 }
 .button3{
       margin-left:44%;
    text-align: center;
     position: relative;
    top:20px;
    height: 100px;
   border: none;
   }
.button3 input{
    background-color:yellow;
      border-color: black;
}
 .btn3{
        margin-left:2%;
          position: relative;
    top:10px;
    }
    </style>
