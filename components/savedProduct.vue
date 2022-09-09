<template>
    <div class="phone">
        <div class="phone-box">
            <p class="name"><b>Name:</b>{{ productData.name }}</p>
            <p class="brand"><b>Brand</b>{{ productData.brand }}</p>
            <p class="price"><b>price:$</b>{{ productData.price }}</p>
            <p class="nickName"><b>Descrioption:</b>{{ productData.description }}</p>
            <p class="nickName"><b>Location:</b>{{ productData.location }}</p>
        </div>
        <button class="delete-btn" @click="$emit('deleteProduct', productData.id)" type="button">Delete</button>
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
            brand: this.productData.brand,
            price: this.productData.price,
            description: this.productData.description,
            location: this.productData.location,
        }
    },
}
</script>

<style scoped>

</style>