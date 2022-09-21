<template>
    <div v-if="productObject" class="information-box">
        <div class="slider-holder">
            <img :src="`data:image/png;base64,${productObject.image.data}`" alt="" class="slider-image" />
        </div>

        <div class="product-detail">
            <h1>{{productObject.name}}</h1>
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
                        <option value="Apple">Apple</option>
                        <option value="Samsung">Samsung</option>
                        <option value="Huawei">Huawei</option>
                        <option value="Oppo">Oppo</option>
                        <option value="Nokia">Nokia</option>
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
            <input class="chat__box--input" placeholder="type message here" type="text" name="message"
                v-model="message">
            <button class="send__button" @click="submitMessage" type="button">Send</button>
        </form>
    </div>
</template>



<script>
import messageContent from '../components/messageContent.vue';
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
            productObject: null,
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
            this.$router.push({ name: 'product', params: { id: this.$route.params.id } })
            this.editing = false;
        },

        async deletePost() {
            const response = await fetch(`http://localhost:3000/products/${this.$route.params.id}`, {
                method: "DELETE"
            });
            const data = await response.json();
            this.$router.push({ name: 'profile' });
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
    padding: 2em 2em 3em 2em;
    margin: auto;
}

.detail-box {
    display: flex;
    align-items: center;
    padding: 0.5em 0;

    label {
        font-family: sans-serif;
        margin-right: 1rem;
    }
}

h3 {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

p {
    font-family: sans-serif;
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
    text-align: center;
    overflow: hidden;
}

.slider-image {
    width: 500px;
    height: 500px;
    object-fit: cover;
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

    p {
        font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    }

    &--buyer {
        display: flex;
        align-items: center;
        gap: 2em;
        margin-left: 2em;
    }

    &--seller {
        display: flex;
        align-items: center;
        gap: 2em;
        margin: 1em 0 0 36em;
    }

    &--form {
        margin-left: 12em;
        margin-top: 1em;
        margin-bottom: 2em;
    }

    &--input {
        height: 30px;
        width: 260px;
    }
}

h1 {
    text-align: center;
    margin: 1em 0;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.profile__img {
    width: 80px;
    height: 80px;
    border-radius: 50px;
}

.profile__comment {
    font-size: 20px;
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

.chat__content {
    height: 400px;
    width: 1000px;
    overflow-y: scroll;
}
</style>