<template>
    <div class="columns-3">
        <div class="item-box">
            <div>
                <img src="../src/image/iphone13.png" alt="">
            </div>
            <div class="subtitle-container">
                <span>{{productData.location}}</span>
                <span>Listed: Thur, 1 Sep</span>
            </div>
            <div class="subtitle-container mb-2">
                <h4>{{productData.name}}</h4>
                <h4>{{productData.id}}</h4>
                <h4>{{productData.description}}</h4>
            </div>
            <div class="subtitle-container">
                <p class="font-blue">48 Watchers</p>
                <p>{{productData.price}}</p>
                <h4>{{productData.price}}</h4>
            </div>
            <div class="subtitle-container">
                <button id="profile-view-button" class="blue-button" type="button">View</button>
                <button @click="$emit('deleteItem', productData.id)" id="profile-delete-button" class="white-button"
                    type="button">Delete</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        productData: Object,
    },
    data() {
        return {
            name: this.productData.name,
            price: this.productData.price,
            location: this.productData.location,
            id: this.productData._id,
            description: this.productData.description
        }
    }
}
</script>

<style scoped>
.column-3 {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}

.item-box {
    min-width: 220px;
    max-width: 260px;
    flex: 1 1 30%;
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

.mb-2 {
    margin-bottom: 1.5em;
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

h3 {
    font-size: 28px;
}

h4 {
    margin-top: 4px;
}

p {
    font-size: 12px;
}

span {
    font-size: 12px;
    color: grey;
    margin-top: 4px;
}

.font-blue {
    color: blue;
}
</style>