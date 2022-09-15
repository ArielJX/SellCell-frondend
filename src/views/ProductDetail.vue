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
                    <p class="name">{{productObject.name}}</p>
                </div>
                <div v-else class="detail-box">
                    <label for="name">Name: </label>
                    <input type="text" id="name" v-model="name">
                </div>
                <div v-if="!editing" class="detail-box">
                    <label for="brand">Brand: </label>
                    <p class="brand">{{productObject.brand}}</p>
                </div>
                <div v-else class="detail-box">
                    <label for="brand">Brand: </label>
                    <select name="brand" id="brand" v-model="brand">
                        <option value="apple">Apple</option>
                        <option value="samsung">Samsung</option>
                        <option value="huawei">Huawei</option>
                        <option value="oppo">Oppo</option>
                        <option value="nokia">Nokia</option>
                    </select>
                </div>
                <div v-if="!editing" class="detail-box">
                    <label for="price">Price: </label>
                    <p class="price">{{productObject.price}}</p>
                </div>
                <div v-else class="detail-box">
                    <label for="price">Price: </label>
                    <input type="text" name="" id="price" v-model="price">
                </div>
            </div>
            <h3>Description</h3>
            <p v-if="!editing" class="description">{{productObject.description}}</p>
            <textarea v-else id="description" cols="40" rows="7" v-model="description"></textarea>
            <h3>Location</h3>
            <p v-if="!editing" class="location">{{productObject.location}}</p>
            <select v-else name="location" id="location" v-model="location">
                <option value="auckland">Auckland</option>
                <option value="hamilton">Hamilton</option>
                <option value="wellington">Wellington</option>
                <option value="Christchurch">Christchurch</option>
            </select>
            <div v-if="!editing" class="buttons">
                <button @click="editPost" class="edit-button" type="button">Edit</button>
                <button class="delete-button" type="button" @click="deletePost">Delete</button>
            </div>
            <div v-else class="buttons">
                <button class="save-button" @click="updatePost" type="button">Save</button>
                <button @click="editing = false" class="cancel-button">Cancel</button>
            </div>
        </div>
    </div>


    <div class="chat__box">
        <h1>Question & Answer</h1>
        <div class="chat__content">
        <div class="chat__box--buyer">
            <img class="profile__img" src="https://wallpaperaccess.com/full/6295120.jpg">
            <p class="profile__comment">Hi does the phone come with a charger?</p>
        </div>

        <div class="chat__box--seller">
            <p class="profile__comment">Yes, it does come with charger :)</p>
            <img class="profile__img" src="https://wallpaperaccess.com/full/3804420.jpg">
        </div>
        <div class="realchat">
            <messageContent v-for="message of messageArray" :message-data="message" :key="message.id" />
        </div>
        </div>

        <form class="chat__box--form">
            <input class="chat__box--input" placeholder="username" type="text" name="username" v-model="username">
            <input class="chat__box--input" placeholder="type message here" type="text" name="message" v-model="message" >
            <button class="send__button" @click="submitMessage" type="button">Send</button>
        </form>
    </div>
</template>



<script>
import messageContent from '../../components/messageContent.vue';
export default {
components: { messageContent },
    data() {
        return {
            editing: false,
            name: null,
            brand: null,
            price: null,
            description: null,
            location: null,
            productObject: {},
            username: null,
            message: null,
            messageArray: []
        }
    },
    methods: {
        editPost() {
            this.editing = true
        },

        async getSinglePost() {
            const response = await fetch(`http://localhost:3000/products/${this.$route.params.id}`);
            const data = await response.json();
            this.productObject = data;
        },

        async updatePost() {
            const response = await fetch(`http://localhost:3000/products/${this.$route.params.id}`, {
                method: "PUT",
                headers: { 'content-type': 'application/json' },
                body: JSON.stringify({
                    name: this.name,
                    brand: this.brand,
                    price: this.price,
                    description: this.description,
                    location: this.location
                })
            });
            const data = await response.json();
            this.productObject = data;
            console.log(this.productObject.name);
            this.$router.push({ name: 'product', params: { id: this.$route.params.id } })
            this.editing = false;
        },

        async deletePost() {
            const response = await fetch(`http://localhost:3000/products/${this.$route.params.id}`, {
                method: "DELETE"
            });
            const data = await response.json();
            this.$router.push({name: 'profile'});
        },
        
        async submitMessage() {
            console.log("submit message");
            const response = await fetch("http://localhost:3000/userMessage", {
                    method: "POST",
                    headers: { "content-type": "application/json" },
                    body: JSON.stringify({
                        username: this.username,
                        message: this.message
                    })
                });
            const data = await response.text();
            this.getMessageLists();

            },
            async getMessageLists() {
            const response = await fetch("http://localhost:3000/userMessage");
            const data = await response.json();
            this.messageArray = data;
    },
    },
    
    mounted() {
        this.getSinglePost();
        this.getMessageLists();    
    }
}
</script>


<style lang="scss" scoped>
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
    left: -500px;
}

#slider-image-3:target~.image-holder {
    left: -1000px;
}

.button-holder {
    position: relative;
    top: -60px;
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
    height: 550px;
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
margin-left: 12em;
margin-top: 1em;
margin-bottom: 2em;
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

.chat__content {
  height: 400px;
  width: 1000px;
  overflow-y: scroll;
}

</style>