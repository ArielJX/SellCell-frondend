<template>
    <div class="item-box center">
        <div class="img-wrapper">
            <img :src="`data:image/png;base64,${findproductData.image.data}`" alt="" />
        </div>
        <div class="subtitle-container">
            <span>{{location}}</span>
            <span>Listed: Thur, 1 Sep</span>
        </div>
        <div class="subtitle-container mb-2">
            <h4>{{name}}</h4>
        </div>
        <div class="subtitle-container">
            <p class="font-blue">48 Watchers</p>
            <p>$ {{price}}</p>
        </div>
        <div class="subtitle-container"><button @click="$router.push(`/ProductforBuyer/${findproductData._id}`)"
                class="blue-button" type="button">View</button></div>
    </div>
</template>

<script>
export default {
    props: {
        findproductData: Object
    },
    data() {
        return {
            name: this.findproductData.name,
            brand: this.findproductData.brand,
            price: this.findproductData.price,
            location: this.findproductData.location,
        }
    },
}

</script>

<style scoped>
.item-box {
    min-width: 220px;
    max-width: 220px;
    flex: 1 1 30%;
    border: 1px solid gainsboro;
    border-radius: 6px;
    padding-bottom: 1em;
}

.img-wrapper {
    width: 100%;
    height: 160px;
}

img {
    width: 100%;
    height: 100%;
    object-fit: cover;
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
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
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

@media screen and (max-width: 680px) {
    .center {
        margin: 0 auto;
        align-self: center;
    }
}
</style>