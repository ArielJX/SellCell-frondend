<template>
    <div class="product-list">
        <h1>List Your Products Here</h1>
        <form @submit.prevent>
            <div class="product-list__name">
                <label for="name">Product Name</label>
                <input type="text" id="name" name="name" v-model="name">
            </div>
            <div class="product-list__brand">
                <label for="brand">Product Brand</label>
                <select name="brand" id="brand" v-model="brand">
                    <option value="apple">Apple</option>
                    <option value="samsung">Samsung</option>
                    <option value="huawei">Huawei</option>
                    <option value="oppo">Oppo</option>
                    <option value="nokia">Nokia</option>
                </select>
            </div>
            <div class="product-list__price">
                <label for="price">Product Price</label>
                <input type="number" id="price" name="price" v-model="price">
            </div>
            <div class="product-list__description">
                <label for="description">Product Description</label>
                <textarea type="text" id="description" name="description" v-model="description" cols="30"
                    rows="5"></textarea>
            </div>
            <div class="product-list__image">
            <label for="image">Product Image</label>
            <input @input="imageSelected" type="file" class="image-link" id="image" >
        </div>
            <div class="product-list__location">
                <label for="location">Product Location</label>
                <select name="location" id="location" v-model="location">
                    <option value="auckland">Auckland</option>
                    <option value="hamilton">Hamilton</option>
                    <option value="wellington">Wellington</option>
                    <option value="Christchurch">Christchurch</option>
                </select>
            </div>
            <button @click="submitForm" type="button">Upload</button>
        </form>
    </div>
</template>

<script>

export default {

    data() {
        return {
            name: null,
            brand: null,
            price: null,
            description: null,
            image: null,
            location: null
        };
    },
    methods: {
        imageSelected(event) {
            this.image = event.target.files[0];
        },
        async submitForm() {
            console.log("submit form");
            const formData = new FormData();
            formData.append('name', this.name);
            formData.append('brand', this.brand);
            formData.append('price', this.price);
            formData.append('description', this.description);
            formData.append('image', this.image);
            formData.append('location', this.location);

            const response = await fetch("http://localhost:3000/products", {
                method: "POST",
                body: formData

            });
            const data = await response.json();
            const savedItemId = data._id;
            this.$router.push({name: 'product', params: {id: savedItemId}});
        },

    },

};
</script>

<style lang="scss" scoped>
.product-list {
    text-align: center;
    padding: 2em 0;
}

h1 {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.product-list div {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 450px;
    margin: auto;
    padding: 0 0 1em 0;
}

.product-list label {
    text-align: start;
    padding: 0.8em 0;
    font-size: 20px;
    font-family: sans-serif;
}

.product-list input {
    padding: 0.3em 0;
}

input[type=number]::-webkit-inner-spin-button {
    appearance: none;
}

.image-link {
    width: 450px;
    height: 50px;
    border: 1px solid rgb(106, 106, 106);
    background-color: rgb(231, 228, 228);
}

.product-list select {
    padding: 0.3em 0;
}


button {
    text-align: center;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: 15px;
    padding: 0.5em 2em;
    margin: 1.5em 0;
    background-color: #1950DA;
    color: white;
    border: none;
    cursor: pointer;
}
</style>