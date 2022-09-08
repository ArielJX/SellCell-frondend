<template>

    <div class="slider-holder">
            <span id="slider-image-1"></span>
            <span id="slider-image-2"></span>
            <span id="slider-image-3"></span>
            <div class="image-holder">
                <img src="https://i.ebayimg.com/images/g/YHEAAOSwE8xhxhIb/s-l500.jpg" class="slider-image" style="width:800px; height: 700px" />
                <img src="https://apollo-singapore.akamaized.net/v1/files/a3lu6gpelqn63-IN/image;s=850x0" class="slider-image" style="width:800px; height: 700px" />
                <img src="https://cellbuddy.in/wp-content/uploads/2021/09/Apple-iPhone-13-Smartphone-491997702-i-2-1200Wx1200H.jpeg" class="slider-image" style="width:800px; height: 700px" />
            </div>
            <div class="button-holder">
                <a href="#slider-image-1" class="slider-change"></a>
                <a href="#slider-image-2" class="slider-change"></a>
                <a href="#slider-image-3" class="slider-change"></a>
            </div>
        </div>

<div class="chat__box">
<h1>Question & Answer</h1>
<div class="chat__box--buyer">
<img class="profile__img" src="https://wallpaperaccess.com/full/6295120.jpg">
<p class="profile__comment" >Hi does the phone come with a charger?</p>
</div>

<div class="chat__box--seller">
<p class="profile__comment" >Yes, it does come with charger :)</p>
<img class="profile__img" src="https://wallpaperaccess.com/full/3804420.jpg">
</div>

<form class="chat__box--form">
<input class="chat__box--input" type="text">
<button class="send__button">Send</button>
</form>
</div>
</template>



<script>
    
</script>



<style scoped>
    .slider-holder {
          width: 800px;
          height: 700px;
          background-color: yellow;
          margin-left: 5em;
          margin-top: 4em;
          text-align: center;
          overflow: hidden;
        }
           
    .image-holder {
          width: 2400px;
          height: 700px;
          clear: both;
          position: relative;
               
          -webkit-transition: left 1s;
          -moz-transition: left 1s;
          -o-transition: left 1s;
          transition: left 1s;
        }
           
    .slider-image {
       float: left;
       margin: 0px;
       padding: 0px;
       position: relative;
      }
    
      a:hover {
        background-color: rgb(193, 193, 193);
      }
    
      a:active {
        background-color: rgb(193, 193, 193)!important;
       }
    
      #slider-image-1:target ~ .image-holder {
        left: 0px;
       }
           
      #slider-image-2:target ~ .image-holder {
        left: -800px;
       }
           
    #slider-image-3:target ~ .image-holder {
        left: -1600px;
    }
           
    .button-holder {
        position: relative;
        top: -40px;
    }
           
    .slider-change {
         display: inline-block;
         height: 20px;
         width: 20px;
         border-radius: 30px;
         border: 3px solid rgb(193, 193, 193);
         background-color: white;
         margin-right: 1em;
    }
    
    
    .chat__box {
        -moz-box-shadow: 3px 3px 5px 6px #ccc;
        -webkit-box-shadow: 3px 3px 5px 6px #ccc;
        box-shadow: 3px 3px 5px 6px #ccc;
        height: 500px;
        width: 1000px;
        margin-top: 20em;
        margin-left: 40em;
        padding: 1em;
    }
    
    h1 {
        text-align: center;
        margin-bottom: 2em;
    }
    
    .chat__box--buyer {
        display: flex;
        gap: 2em;
        margin-left: 2em;
    }
    .chat__box--seller {
        display: flex;
        gap: 2em;
        margin: 1em 0 0 36em;
    }
    .profile__img {
        width: 80px;
        height: 80px;
        border-radius: 50px;
    }
    
    .profile__comment {
        font-size: 20px;
    }
    
    .chat__box--form {
        position: relative;
        left: 30%;
        top: 28%;
    }
    
    .send__button {
        border: none;
        background-color: rgba(25, 80, 218, 1);
        color: white;
        width: 60px;
        height: 36px; 
        margin-left: 1em;
        font-size: 16px;
        box-sizing: border-box;
    }
    
    .chat__box--input {
        height: 30px;
        width: 260px;
    }
    </style>