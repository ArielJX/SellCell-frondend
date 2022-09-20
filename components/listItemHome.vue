<template>
    <div class="phone">
        <div class="phone-box">
            <img :src="`data:image/png;base64,${productData.image.data}`" alt=""/>
            <p class="name">{{ productData.name }}</p>
            <p class="brand"><b>Brand:</b>{{ productData.brand }}</p>
            <p class="price"><b>Price:$</b>{{ productData.price }}</p>
            <p class="location"><b>Location:</b>{{ productData.location }}</p>
        </div>
        <button @click="$router.push(`/ProductforBuyer/${productData._id}`)" class="detail-btn" type="button">See details</button>
    </div>
</template>

<script>
export default {
    props: {
        productData: Object
    },
    data() {
        return {
            name: this.productData.name,
            brand: this.productData.brand,
            price: this.productData.price,
            location: this.productData.location,
        }
    },
}

</script>

<style scoped>
    .phone {
        justify-content: center;
        text-align: center;
    }
    img {
        height: 100px;
        width: 80px;
        object-fit: cover;
    }
.phone-box {
    border: 1px solid gainsboro;
    border-radius: 6px;
    text-align: center;
    margin-right: 2em;
    padding: 2em 4em;
}
.detail-btn {
  margin-top: 2em;
  color: white;
  background-color: #1950DA;
  border: none;
  border-radius: 2px;
  padding: 1em 2em;
  margin-bottom: 2em;
  font-size: 12px;
}
</style>