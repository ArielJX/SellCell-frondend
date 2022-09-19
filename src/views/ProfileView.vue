<template>
    <div class="profile">
        <div class="profile-left">
            <div class="profile-bg-wrapper">
                <h2 class="white-h2">Welcome Back Sharon</h2>
            </div>
            <div class="border-container">
                <div class="title-container">
                    <h3 class="center">Sell items Listings</h3>
                    <button id="profile-list-button" class="white-button center" type="button"
                        @click="$router.push('listProduct')">List new item</button>
                </div>
                <div class="column-3 center">
                    <ProfileItem @delete-item="deleteItem" v-for="product of productArray" :product-data="product"
                        :key="product.id" />

                </div>
            </div>
        </div>
        <div class="profile-right">
            <div class="img-wrapper center"></div>
            <div class="profile-detail center">
                <h3 class="center">Sharon Smith</h3>
                <div class="stars center">
                    <img class="star" src="../image/star-solid.svg" alt="">
                    <img class="star" src="../image/star-solid.svg" alt="">
                    <img class="star" src="../image/star-solid.svg" alt="">
                    <img class="star" src="../image/star-solid.svg" alt="">
                    <img class="star" src="../image/star-solid.svg" alt="">
                </div>
                <span class="center">Sellers Rate</span>
            </div>
            <div class="profile-detail--location center">
                <div class="detail-container">
                    <p>Location</p>
                    <p>North Shore</p>
                </div>
                <div class="detail-container">
                    <p>Member Since</p>
                    <p>2009</p>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import ProfileItem from "../../components/profileItem.vue";
export default {
    components: {
        ProfileItem,
    },
    data() {
        return {
            name: null,
            price: null,
            location: null,
            productArray: []
        };
    },
    methods: {
        async getItem() {
            const response = await fetch(`http://localhost:3000/products`);
            const data = await response.json();
            this.productArray = data;
        },
        async deleteItem(id) {
            const response = await fetch(`http://localhost:3000/products/${id}`, {
                method: "DELETE"
            });
            const data = await response.json();

            this.getItem();
        },
       
    },
    mounted() {
        this.getItem();
    }
}
</script>

<style scoped>
.profile {
    min-width: 400px;
    width: 100%;
    margin: 0 auto;
    display: flex;
    flex-direction: row;
}

.profile-left {
    width: 80%;
    padding: 0 1rem;
}

.profile-bg-wrapper {
    width: 100%;
    height: 220px;
    margin-bottom: 2rem;
    background-image: url(../image/profile-bg.jpg);
    background-repeat: none;
    background-size: cover;
    border-radius: 10px;
    display: flex;

}

.white-h2 {
    color: white;
    font-size: 38px;
    margin: 4px auto;
    align-self: center;
    text-shadow: 4px 4px 6px black;;
}

.border-container {
    border: 1px solid gainsboro;
    border-radius: 10px;
    padding: 1rem 3rem 4rem 3rem;
}

.title-container {
    display: flex;
    flex-direction: row;
    align-content: center;
    gap: 2rem;
}

.column-3 {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    gap: 1em;

}

.item-box {
    max-width: 240px;
    flex: 1 1 30%;
    border: 1px solid gainsboro;
    border-radius: 6px;
    padding-bottom: 1em;
}

img {
    width: 100%;
    border-radius: 6px 6px;
}

.subtitle-container {
    padding: 0 1em;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.profile-right {
    width: 20%;
    padding: 0 1rem;
    display: flex;
    flex-direction: column;
}

.profile-detail {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-bottom: 2rem;
}

/* .center {
    margin: 4px auto;
    align-self: center;
} */

.img-wrapper {
    width: 160px;
    height: 160px;
    border-radius: 50%;
    background-image: url(../image/user-img.png);
    background-repeat: none;
    background-size: cover;
    background-position: center;
}

.profile-detail--location {
    width: 100%;
}

.detail-container {
    padding: 0;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    border-bottom: 1px solid gainsboro;
}

.stars {
    display: flex;
    flex-direction: row;
    justify-content: center;
}

.star {
    width: 8%;
}

.mb-2 {
    margin-bottom: 1.5em;
}

h3 {
    font-size: 26px;
}

h4 {
    margin-top: 4px;
}

p {
    font-size: 12px;
}

.font-blue {
    color: blue;
}

span {
    font-size: 12px;
    color: grey;
    margin-top: 4px;
}

button {
    height: 24px;
    margin: auto 6px;
}

button:hover {
    cursor: pointer;
}

.blue-button {
    color: white;
    background-color: #1950DA;
    border: none;
    border-radius: 4px;
    padding: 4px 1.5em;
}

.white-button {
    color: #1950DA;
    background: white;
    border: #1950DA 1px solid;
    border-radius: 4px;
    padding: 4px 1em;
    width: 120px;
}

@media screen and (max-width: 680px) {
    .profile-right {
        display: none;
    }

    .profile-left {
        width: 100%;
    }

    .title-container {
        flex-direction: column;
        gap: 0;
        margin-bottom: 2rem;
    }

    .center {
        margin: 4px auto;
        align-self: center;
    }

    .border-container {
        padding: 1rem 0px;
    }
}
</style>