<template>
    <div class="list-product">
        <div class="item-box">
        <div>
            <img class="productImage" :src="productData.image" alt="productData Image">
            <!--insert image link-->
        </div>
        <div class="subtitle-container">
            <span>{{productData.name}}</span>
            <span>Listed: Thur, 1 Sep</span>
        </div>
        <div class="subtitle-container mb-2">
            <h4>{{productData.description}}</h4>
        </div>
        <div class="subtitle-container underline">
            <p class="font-blue">48 Watchers</p>
            <p>Price by negotiation</p>
        </div>
        <div class="subtitle-container">
            <button id="profile-view-button" class="blue-button" type="button" @click="$router.push('product')">View</button>
            <button class="btn-delete" @click="$emit('deleteProduct', productData.id)" type="button">Delete</button>
        </div>
    </div>
    </div>
</template>

<script>
    export default {
        components: { productData },
        props: {
            productData: Object,
        },
        data() {
            return {
            name: this.productData.name,
            brand: this.productData.brand,
            price: this.productData.price,
            description: this.productData.description,
            location: this.productData.location,

            newProductData: {
            name: null,
            brand: null,
            price: null,
            description: null,
            location: null
            }
            }
        },
        methods: {

        }
    }
</script>

<style lang="scss" scoped>

</style>