<template>
    <div class="container">
        <div v-if="productObject" class="information-box">
            <div class="slider-holder">
                <img :src="`data:image/png;base64,${productObject.image.data}`" alt="" class="slider-image" />
            </div>

            <div class="product-detail">
                <h1>Iphone X</h1>
                <div class="product-details">
                    <div class="detail-box">
                        <label for="name">Name: </label>
                        <p class="name">{{productObject.name}}</p>
                    </div>
                    <div class="detail-box">
                        <label for="brand">Brand: </label>
                        <p class="brand">{{productObject.brand}}</p>
                    </div>
                    <div class="detail-box">
                        <label for="price">Price: </label>
                        <p class="price">{{productObject.price}}</p>
                    </div>
                </div>
                <h3>Description</h3>
                <p class="description">{{productObject.description}}</p>
                <h3>Location</h3>
                <p class="location">{{productObject.location}}</p>
                <div class="dropdown">
            <button class="seller__button">Seller info</button>
            <div class="dropdown-content">
            <p>Username: Grace0126</p>
            <p>Contact: Grace@hotmail.com</p>
            <p style="color:green;">Authenticated account</p>
            </div>
            </div>
            </div>
        </div>
    </div>
    <div class="container">
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
    </div>
</template>

<script>
import messageContent from '../components/messageContent.vue';
export default {
    components: { messageContent },
    data() {
        return {
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
        async getSinglePost() {
            const response = await fetch(`http://localhost:3000/products/${this.$route.params.id}`);
            const data = await response.json();
            this.productObject = data;
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
$main-blue: #184DD1;
$dark-blue: #003489;
$white: white;

@mixin btn-theme-blue {
  display: inline-block;
  justify-content: center;
  margin-top: 1rem;
  padding: 12px 1em;
  background: $main-blue;
  color: $white;
  cursor: pointer;
  border-radius: .3rem;
  text-align: center;
  font-size: 14px;
  border: 1px solid white;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;

  &:hover {
    background: $dark-blue;
  }
}

@mixin btn-theme2 {
    border: none;
    background-color: rgba(25, 80, 218, 1);
    color: white;
    width: 60px;
    height: 36px;
    font-size: 16px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}

@mixin btn-theme-green {
    border: none;
    background-color: #17A500;
    color: white;
    width: 60px;
    height: 36px;
    font-size: 16px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    cursor: pointer;
}

.container {
    width: 100%;
    padding-top: 2rem;
}

h1 {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    text-align: center;
    margin: 0 0 1em 0;

}

.information-box {
    width: 100%;
    max-width: 1000px;
    margin: 0 auto 4rem auto;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 2rem;

    .slider-holder {
        width: 50%;
        min-width: 160px;
        height: 450px;
        text-align: center;
        overflow: hidden;
        margin-left: 4rem;

        .slider-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

    .product-detail {
        width: 50%;
        max-width: 400px;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: flex-start;

        .product-details {
            padding-right: 1rem;

            .detail-box {
                display: flex;
                align-items: center;

                label {
                    font-family: sans-serif;
                    margin-right: 1rem;
                }

                p,
                label {
                    margin-bottom: 3px;
                }
            }
        }
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



.chat__box {
    box-shadow: 3px 3px 5px 6px #ccc;
    width: 100%;
    max-width: 1000px;
    height: 550px;
    margin: 0 auto 4em auto;
    display: flex;
    flex-direction: column;
    gap: 2rem;



    p {
        font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    }

    &--buyer {
        width: 100%;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        gap: 2em;
    }

    &--seller {
        width: 100%;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        gap: 2em;
    }

    &--form {
        height: 30px;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 8px;
        margin-bottom: 12px;
    }

    &--input {
        height: 30px;
        width: 30%;
    }
}

.chat__content {
    height: 400px;
    padding: 1rem;
    overflow-y: scroll;
}

.profile__img {
    width: 80px;
    height: 80px;
    border-radius: 50px;
}

.profile__comment {
    font-size: 20px;
}

button {
    border-radius: 2px;
}

.send__button {
@include btn-theme-blue;
}

@media (max-width: 700px) {

    h1 {
        font-size: 22px;
    }

    h3 {
        font-size: 16px;
        margin: 8px 0;
    }

    p,
    label {
        font-size: 12px;
    }

    .information-box {
        gap: 1rem;

        .slider-holder {
            height: 220px;
            margin-left: 2.5rem;
        }

        .product-detail {
            width: 40%
        }
    }

    .detail-box {
        padding: 0;
    }

    .send__button {
        width: 50px;
        height: 32px;
    }

    .chat__box {
        height: 300px;
        max-width: 80%;
    }

    .profile__img {
        width: 45px;
        height: 45px;
    }

    .profile__comment {
        font-size: 12px;
    }
}

.dropdown {
  position: relative;
  display: inline-block;
}
 .seller__button {
    @include btn-theme-blue;
  }

.dropdown-content {
  display: none;
  position: absolute;
  background-color: $white;
  width: 300px;
  height: 100px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown:hover .dropdown-content {display: block;}
.dropdown:hover .dropbtn {background-color: $main-blue;}
</style>