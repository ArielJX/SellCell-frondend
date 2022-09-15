<template>
  <div class="item-box">
    <div>
      <img src="../image/iphone13.png" alt="">
    </div>
    <div class="subtitle-container">
      <span>{{productData.location}}</span>
      <span>Listed: Thur, 1 Sep</span>
    </div>
    <div class="subtitle-container mb-2">
      <h4>{{productData.name}}</h4>
    </div>
    <div class="subtitle-container">
      <p class="font-blue">48 Watchers</p>
      <p>{{productData.price}}</p>
    </div>
    <div class="subtitle-container">
      <button id="profile-view-button" class="blue-button" type="button" @click="$router.push('product')">View</button>
      <button id="profile-delete-button" class="white-button" type="button"
        @click="$emit('deleteProduct', productData.id)">Delete</button>
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
      location: this.productData.location,
      price: this.productData.price,
    }
  },
}
</script>

<style scoped>
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

.mb-2 {
  margin-bottom: 1.5em;
}

.font-blue {
  color: blue;
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