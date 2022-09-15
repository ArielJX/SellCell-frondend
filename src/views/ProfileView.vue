<template>
    <div class="profile">
        <div class="profile-left">
            <div class="profile-bg-wrapper">
                <h2 class="white-h2">Welcome Back Sharon</h2>
            </div>
            <div class="border-container">
                <div class="title-container">
                    <h3>Sell items Listings</h3>
                    <button id="profile-list-button" class="white-button" type="button" @click="$router.push('listProduct')">List new item</button>
                </div>
                <div class="listing-box column-3">
                    <div class="item-box">
                        <div>
                            <img src="../image/iphone13.png" alt="">
                        </div>
                        <div class="subtitle-container">
                            <span>Auckland</span>
                            <span>Listed: Thur, 1 Sep</span>
                        </div>
                        <div class="subtitle-container mb-2">
                            <h4>Iphone 13 pro, 99% new</h4>
                        </div>
                        <div class="subtitle-container underline">
                            <p class="font-blue">48 Watchers</p>
                            <p>Price by negotiation</p>
                        </div>
                        <div class="subtitle-container">
                            <button id="profile-view-button" class="blue-button" type="button" @click="$router.push('product')">View</button>
                            <button id="profile-delete-button" class="white-button" type="button">Delete</button>
                        </div>
                    </div>
                    <div class="item-box">
                        <div>
                            <img src="../image/iphone13.png" alt="">
                        </div>
                        <div class="subtitle-container">
                            <span>Auckland</span>
                            <span>Listed: Thur, 1 Sep</span>
                        </div>
                        <div class="subtitle-container mb-2">
                            <h4>Iphone 13 pro, 99% new</h4>
                        </div>
                        <div class="subtitle-container underline">
                            <p class="font-blue">48 Watchers</p>
                            <p>Price by negotiation</p>
                        </div>
                        <div class="subtitle-container">
                            <button id="profile-view-button" class="blue-button" type="button">View</button>
                            <button id="profile-delete-button" class="white-button" type="button">Delete</button>
                        </div>
                    </div>
                    <div class="item-box">
                        <div>
                            <img src="../image/iphone13.png" alt="">
                        </div>
                        <div class="subtitle-container">
                            <span>Auckland</span>
                            <span>Listed: Thur, 1 Sep</span>
                        </div>
                        <div class="subtitle-container mb-2">
                            <h4>Iphone 13 pro, 99% new</h4>
                        </div>
                        <div class="subtitle-container underline">
                            <p class="font-blue">48 Watchers</p>
                            <p>Price by negotiation</p>
                        </div>
                        <div class="subtitle-container">
                            <button id="profile-view-button" class="blue-button" type="button">View</button>
                            <button id="profile-delete-button" class="white-button" type="button">Delete</button>
                        </div>
                    </div>
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
import listProduct from '../../components/profileItem.vue';
export default {

}
</script>

<style scoped>
.profile {
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
    position: relative;
}

.white-h2 {
    color: white;
    font-size: 2em;
    position: absolute;
    top: 25%;
    left: 10%;
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
    display: grid;
    grid-template-columns: repeat(3, minmax(100px, 1fr));
    grid-gap: 1em;
}

.item-box {
    border: 1px solid gainsboro;
    border-radius: 6px;
    padding-bottom: 1em;
}

img {
    width: 100%;
    border-radius: 6px;
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

.center {
    align-self: center;
}

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
    font-size: 28px;
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
}
</style>