<template>
    <div class="phone">
        <div class="phone-box">
            <p class="name"><b>Name:</b>{{ findproductData.name }}</p>
            <p class="brand"><b>Brand</b>{{ findproductData.brand }}</p>
            <p class="price"><b>price:$</b>{{ findproductData.price }}</p>
            <p class="nickName"><b>Description:</b>{{ findproductData.description }}</p>
            <p class="nickName"><b>Location:</b>{{ findproductData.location }}</p>
        </div>
        <button class="detail-btn" type="button">See details</button>
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
            description: this.findproductData.description,
            location: this.findproductData.location,
        }
    },
}

</script>

<style scoped>
    .phone {
        justify-content: center;
        text-align: center;
    }
    .photo, .image {
        height: 80px;
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