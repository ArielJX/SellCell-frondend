<template>
    <div class="information-box">
        <div class="slider-holder">
        <span id="slider-image-1"></span>
        <span id="slider-image-2"></span>
        <span id="slider-image-3"></span>
        <div class="image-holder">
            <img src="https://i.ebayimg.com/images/g/YHEAAOSwE8xhxhIb/s-l500.jpg" class="slider-image"
                style="width:500px; height: 500px" />
            <img src="https://apollo-singapore.akamaized.net/v1/files/a3lu6gpelqn63-IN/image;s=850x0"
                class="slider-image" style="width:500px; height: 500px" />
            <img src="https://cellbuddy.in/wp-content/uploads/2021/09/Apple-iPhone-13-Smartphone-491997702-i-2-1200Wx1200H.jpeg"
                class="slider-image" style="width:500px; height: 500px" />
        </div>
        <div class="button-holder">
            <a href="#slider-image-1" class="slider-change"></a>
            <a href="#slider-image-2" class="slider-change"></a>
            <a href="#slider-image-3" class="slider-change"></a>
        </div>
    </div>
    <div class="product-detail">
        <h1>Iphone X</h1>
        <h3>Details</h3>
        <div class="product-details">
            <div v-if="!editing" class="detail-box">
                <label for="name">Name: </label>
                <p class="name">iphoneX</p>
            </div>
            <div v-else class="detail-box">
                <label for="name">Name: </label>
                <input type="text" id="name">
            </div>
            <div v-if="!editing" class="detail-box">
                <label for="brand">Brand: </label>
                <p class="brand">iphone</p> 
            </div>
            <div v-else class="detail-box">
                <label for="brand">Brand: </label>
                <select name="brand" id="brand">
                <option value="apple">Apple</option>
                <option value="samsung">Samsung</option>
                <option value="huawei">Huawei</option>
                <option value="oppo">Oppo</option>
                <option value="nokia">Nokia</option>
            </select>
            </div>
            <div v-if="!editing" class="detail-box">
                <label for="price">Price: </label>
                <p class="price">1000</p>
            </div>
            <div v-else class="detail-box">
                <label for="price">Price: </label>
                <input type="text" name="" id="price">
            </div>
        </div>
        <h3>Description</h3>
        <p v-if="!editing" class="description">phone 13 used for 3 years, in excellent condition. No scratches or previous damage. I still have 1 year of warrantee left with receipt. Please contact me if you have any questions. No negotiations. </p>
        <textarea v-else id="description" cols="40" rows="7"></textarea>
        <h3>Location</h3>
        <p v-if="!editing" class="location">Auckland</p>
        <select v-else name="location" id="location">
                <option value="auckland">Auckland</option>
                <option value="hamilton">Hamilton</option>
                <option value="wellington">Wellington</option>
                <option value="Christchurch">Christchurch</option>
            </select>
        <div v-if="!editing" class="buttons">
            <button @click="editPost" class="edit-button">Edit</button>
            <button class="delete-button">Delete</button>
        </div>
        <div v-else class="buttons">
            <button  class="save-button">Save</button>
            <button @click="editing = false" class="cancel-button">Cancel</button>
        </div>
    </div>
    </div>
    

    <div class="chat__box">
        <h1>Question & Answer</h1>
        <div class="chat__box--buyer">
            <img class="profile__img" src="https://wallpaperaccess.com/full/6295120.jpg">
            <p class="profile__comment">Hi does the phone come with a charger?</p>
        </div>

        <div class="chat__box--seller">
            <p class="profile__comment">Yes, it does come with charger :)</p>
            <img class="profile__img" src="https://wallpaperaccess.com/full/3804420.jpg">
        </div>

        <form class="chat__box--form">
            <input class="chat__box--input" type="text">
            <button class="send__button">Send</button>
        </form>
    </div>
</template>



<script>
    export default {
        data() {
            return {
                editing: false
            }
        },
        methods: {
            editPost() {
                this.editing = true
            }
        }
    }
</script>



<style scoped>
    .information-box {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 1000px;
        padding:2em 2em 3em 2em;
        margin: auto;
    }


    .detail-box {
        display: flex;
        align-items: center;
        padding: 0.5em 0;
    }

    p {
        font-size: 18px;
        margin: 0;
    }
.product-detail {
    width: 400px;
}    

.buttons {
    width: 200px;
    display: flex;
    justify-content: space-between;
    margin: auto;
    padding-top: 1em;
}

.edit-button {
    border: none;
    background-color: rgba(25, 80, 218, 1);
    color: white;
    width: 60px;
    height: 36px;
    font-size: 16px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}
.save-button {
    border: none;
    background-color: rgba(25, 80, 218, 1);
    color: white;
    width: 60px;
    height: 36px;
    font-size: 16px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}
.delete-button {
    border: none;
    background-color: #17A500;
    color: white;
    width: 60px;
    height: 36px;
    font-size: 16px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}
.cancel-button {
    border: none;
    background-color: #17A500;
    color: white;
    width: 60px;
    height: 36px;
    font-size: 16px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}
.slider-holder {
    width: 500px;
    height: 500px;
    background-color: yellow;
    text-align: center;
    overflow: hidden;
}

.image-holder {
    width: 1500px;
    height: 500px;
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
    background-color: rgb(193, 193, 193) !important;
}

#slider-image-1:target~.image-holder {
    left: 0px;
}

#slider-image-2:target~.image-holder {
    left: -800px;
}

#slider-image-3:target~.image-holder {
    left: -1600px;
}

.button-holder {
    position: relative;
    top: -31px;
}


.slider-change {
    display: inline-block;
    height: 15px;
    width: 15px;
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
    margin: auto;
    margin-bottom: 4em;
    padding: 2em;
}

h1 {
    text-align: center;
    margin: 1em 0;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.chat__box--buyer {
    display: flex;
    align-items: center;
    gap: 2em;
    margin-left: 2em;
}

.chat__box--seller {
    display: flex;
    align-items: center;
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
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}

.chat__box--input {
    height: 30px;
    width: 260px;
}
</style>