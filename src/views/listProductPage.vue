<template>
    <div class="product-list">
        <h1>List Your Products Here</h1>
        <form>
            <div class="product-list__name">
                <label for="name">Product Name</label>
                <input type="text" id="name" name="name" v-model="name">
            </div>
            <div class="product-list__brand">
                <label for="brand">Product Brand</label>
                <select name="brand" id="brand" v-model="brand">
                    <option value="Apple">Apple</option>
                    <option value="Samsung">Samsung</option>
                    <option value="Huawei">Huawei</option>
                    <option value="Oppo">Oppo</option>
                    <option value="Nokia">Nokia</option>
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
            <!-- <div class="product-list__image">
            <label for="image">Product Image</label>
            <input type="image" class="image-link" id="image" alt="upload" src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNzUycHQiIGhlaWdodD0iNzUycHQiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDc1MiA3NTIiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CiA8Zz4KICA8cGF0aCBkPSJtNTUzLjEgMzYxLjExdi0xNDYuOTJjMC0yNi42MTctMjEuNjUyLTQ4LjI3LTQ4LjI3LTQ4LjI3aC0zMTMuNjZjLTI2LjYxNyAwLTQ4LjI3IDIxLjY1Mi00OC4yNyA0OC4yN3YyNTYuNGMwIDI2LjYxNyAyMS42NTIgNDguMjcgNDguMjcgNDguMjdoMTg2LjU1YzIwLjE5NSAzOS44MDkgNjEuNDQ5IDY3LjIxOSAxMDkuMDYgNjcuMjE5IDY3LjQ1MyAwIDEyMi4zMy01NC44NzkgMTIyLjMzLTEyMi4zMyAwLTQzLjAwNC0yMi4zNTItODAuODI0LTU2LjAwOC0xMDIuNjR6bS0zNjEuOTMgMTM1Ljg5Yy0xNC41NjIgMC0yNi40MS0xMS44NDgtMjYuNDEtMjYuNDFsLTAuMDAzOTA2LTI1Ni40YzAtMTQuNTYyIDExLjg0OC0yNi40MSAyNi40MS0yNi40MWgzMTMuNjZjMTQuNTYyIDAgMjYuNDEgMTEuODQ4IDI2LjQxIDI2LjQxdjEzNS43MmMtMTMuODA5LTUuNDE0MS0yOC43NjYtOC40ODgzLTQ0LjQ2NS04LjQ4ODMtNy4yMDcgMC0xNC4yMyAwLjc1LTIxLjEwMiAxLjk1MzFsLTM1LjYyOS0yOC45NjFjLTAuMDUwNzgxLTAuMDM1MTU3LTAuMTAxNTYtMC4wNTg1OTQtMC4xNTIzNC0wLjEwMTU2LTAuMzA0NjktMC4yNDIxOS0wLjYzMjgxLTAuNDI5NjktMC45NjA5NC0wLjYzMjgxLTAuMjk2ODgtMC4xODc1LTAuNTgyMDMtMC4zOTQ1My0wLjg5NDUzLTAuNTQ2ODgtMC4yMzQzOC0wLjExNzE5LTAuNDgwNDctMC4xODc1LTAuNzMwNDctMC4yOTI5Ny0wLjQyMTg4LTAuMTc1NzgtMC44MzU5NC0wLjM1NTQ3LTEuMjczNC0wLjQ4MDQ3LTAuMTYwMTYtMC4wNDI5NjktMC4zMzU5NC0wLjA1MDc4MS0wLjUwMzkxLTAuMDkzNzUtMC41MTE3Mi0wLjExNzE5LTEuMDM1Mi0wLjIyNjU2LTEuNTUwOC0wLjI2MTcyLTAuMjAzMTItMC4wMTU2MjQtMC40MjE4NyAwLjAwNzgxMy0wLjYyNSAwLTAuNDgwNDctMC4wMDc4MTItMC45Njg3NS0wLjAyMzQzNy0xLjQ0OTIgMC4wMzUxNTctMC4yNjE3MiAwLjAyNzM0My0wLjUxNTYyIDAuMTA5MzgtMC43ODEyNSAwLjE1MjM0LTAuNDM3NSAwLjA4MjAzMi0wLjg2NzE5IDAuMTUyMzQtMS4yODkxIDAuMjkyOTctMC4yNDIxOSAwLjA4MjAzMS0wLjQ3MjY2IDAuMTk1MzEtMC43MjI2NiAwLjI5Njg4LTAuNDM3NSAwLjE2Nzk3LTAuODU5MzggMC4zNDM3NS0xLjI3MzQgMC41NjY0MS0wLjA0Mjk2OSAwLjAyNzM0NC0wLjA5Mzc1IDAuMDM1MTU3LTAuMTM2NzIgMC4wNjY0MDdsLTQ5LjQ4NCAyOC40MzgtNTguODI0LTU0LjgxMmMtMC4wNTg1OTQtMC4wNTg1OTQtMC4xNDQ1My0wLjA3NDIxOS0wLjIwMzEyLTAuMTI1LTAuOTkyMTktMC44OTA2Mi0yLjA5NzctMS41NTA4LTMuMjg1Mi0yLjAxOTUtMC4xNDQ1My0wLjA1ODU5NC0wLjI4NTE2LTAuMTE3MTktMC40Mjk2OS0wLjE2Nzk3LTEuMTg3NS0wLjQwNjI1LTIuNDEwMi0wLjU5NzY2LTMuNjU2Mi0wLjU4MjAzLTAuMTYwMTYgMC0wLjMyMDMxIDAtMC40ODA0NyAwLjAwNzgxMi0xLjIxNDggMC4wNjY0MDYtMi40MTggMC4zNTE1Ni0zLjU3MDMgMC44MzIwMy0wLjE2Nzk3IDAuMDY2NDA3LTAuMzI4MTIgMC4xMzI4MS0wLjQ5NjA5IDAuMjEwOTQtMC44NDM3NSAwLjQwMjM0LTEuNjYwMiAwLjg4MjgxLTIuNDEwMiAxLjUxNTZsLTExMS40IDk0LjcyM2MtNC41OTc3IDMuOTA2Mi01LjE2MDIgMTAuODA1LTEuMjQ2MSAxNS40MDIgMi4xNTYyIDIuNTQzIDUuMjM4MyAzLjg0NzcgOC4zMjgxIDMuODQ3NyAyLjUwNzggMCA1LjAxOTUtMC44NTE1NiA3LjA3NDItMi42MDE2bDEwNC04OC40MyA4Ny4xNDEgODEuMjA3Yy0xNS4xOTkgMjAuMzg3LTI0LjMyIDQ1LjU2Ni0yNC4zMiA3Mi44ODcgMCAxMS41MzkgMS43MTA5IDIyLjY2IDQuNzE0OCAzMy4yNTR6bTIxMi4xNi0xMjIuNDUtMTguMzY3LTE3LjExMyAzNy4xMzctMjEuMzMyIDE3Ljk4OCAxNC42MTdjLTEzLjcwNyA1LjY4NzUtMjYuMDg2IDEzLjg0LTM2Ljc1OCAyMy44Mjh6bTgzLjQ1MyAxODkuNjZjLTU1LjQwMiAwLTEwMC40Ny00NS4wNzgtMTAwLjQ3LTEwMC40N3M0NS4wNzgtMTAwLjQ3IDEwMC40Ny0xMDAuNDdjNTUuMzk1IDAgMTAwLjQ3IDQ1LjA3OCAxMDAuNDcgMTAwLjQ3LTAuMDAzOTA2IDU1LjM5OC00NS4wNzQgMTAwLjQ3LTEwMC40NyAxMDAuNDd6Ii8+CiAgPHBhdGggZD0ibTIyNS43IDI5MS43MmMyNS40MTQgMCA0Ni4wOS0yMC42NzYgNDYuMDktNDYuMDkgMC0yNS40MTQtMjAuNjc2LTQ2LjA5LTQ2LjA5LTQ2LjA5cy00Ni4wOSAyMC42NzYtNDYuMDkgNDYuMDljLTAuMDAzOTA2IDI1LjQxNCAyMC42NzYgNDYuMDkgNDYuMDkgNDYuMDl6bTAtNzAuMzMyYzEzLjM2MyAwIDI0LjIzNCAxMC44NzEgMjQuMjM0IDI0LjIzNCAwIDEzLjM2My0xMC44NzEgMjQuMjM0LTI0LjIzNCAyNC4yMzRzLTI0LjIzNC0xMC44NzEtMjQuMjM0LTI0LjIzNGMwLTEzLjM2MyAxMC44NzEtMjQuMjM0IDI0LjIzNC0yNC4yMzR6Ii8+CiAgPHBhdGggZD0ibTQ5My44MyA0MDIuNTdjLTAuMDQyOTY5LTAuMDM1MTU3LTAuMDkzNzUtMC4wNTg1OTQtMC4xNDQ1My0wLjA5Mzc1LTAuMTUyMzQtMC4xMzY3Mi0wLjMyODEyLTAuMjQ2MDktMC40ODgyOC0wLjM3MTA5LTAuMjUzOTEtMC4xODM1OS0wLjUyMzQ0LTAuMzU1NDctMC43OTI5Ny0wLjUxNTYyLTAuMTc1NzgtMC4xMDkzOC0wLjM0Mzc1LTAuMjI2NTYtMC41MjM0NC0wLjMyODEyLTAuMTYwMTYtMC4wODU5MzctMC4zNDM3NS0wLjE1MjM0LTAuNTAzOTEtMC4yMzQzOC0wLjI4NTE2LTAuMTMyODEtMC41NjY0MS0wLjIzNDM4LTAuODU5MzgtMC4zNDM3NS0wLjIwMzEyLTAuMDgyMDMxLTAuNDA2MjUtMC4xNjc5Ny0wLjYyMTA5LTAuMjM0MzgtMC4xNjc5Ny0wLjA1MDc4MS0wLjM1MTU2LTAuMDgyMDMxLTAuNTE1NjItMC4xMjUtMC4yOTI5Ny0wLjA3NDIxOS0wLjU4OTg0LTAuMTI1LTAuODkwNjItMC4xNjc5Ny0wLjIxODc1LTAuMDM1MTU2LTAuNDM3NS0wLjA4NTkzNy0wLjY1NjI1LTAuMTA5MzgtMC4xOTUzMS0wLjAyMzQzNy0wLjQwNjI1LTAuMDE1NjI1LTAuNjA1NDctMC4wMjM0MzctMC4xNTIzNC0wLjAwNzgxMy0wLjI5Mjk3LTAuMDQyOTY5LTAuNDQ1MzEtMC4wNDI5NjlzLTAuMjkyOTcgMC4wMzUxNTYtMC40NDUzMSAwLjA0Mjk2OWMtMC4xOTUzMSAwLjAwNzgxMi0wLjQwNjI1IDAtMC42MDU0NyAwLjAyMzQzNy0wLjIxODc1IDAuMDIzNDM4LTAuNDM3NSAwLjA3NDIxOS0wLjY1NjI1IDAuMTA5MzgtMC4yOTY4OCAwLjA1MDc4Mi0wLjU5NzY2IDAuMTAxNTYtMC44OTA2MiAwLjE2Nzk3LTAuMTY3OTcgMC4wNDI5NjktMC4zNTE1NiAwLjA3NDIxOS0wLjUxNTYyIDAuMTI1LTAuMjEwOTQgMC4wNjY0MDYtMC40MTQwNiAwLjE1MjM0LTAuNjIxMDkgMC4yMzQzOC0wLjI5Mjk3IDAuMTA5MzgtMC41NzQyMiAwLjIxMDk0LTAuODU5MzggMC4zNDM3NS0wLjE2MDE2IDAuMDgyMDMxLTAuMzM1OTQgMC4xNTIzNC0wLjUwMzkxIDAuMjM0MzgtMC4xNzU3OCAwLjEwMTU2LTAuMzUxNTYgMC4yMTg3NS0wLjUzMTI1IDAuMzI4MTItMC4yNjk1MyAwLjE2MDE2LTAuNTMxMjUgMC4zMzU5NC0wLjc4MTI1IDAuNTE1NjItMC4xNjc5NyAwLjEyNS0wLjM0Mzc1IDAuMjM0MzgtMC40OTYwOSAwLjM3MTA5LTAuMDUwNzgxIDAuMDM1MTU2LTAuMTAxNTYgMC4wNTg1OTMtMC4xNDQ1MyAwLjA5Mzc1bC00My44NjcgMzcuMDQ3Yy00LjYxMzMgMy44OTA2LTUuMTk1MyAxMC43ODEtMS4yOTY5IDE1LjM5NSAyLjE1NjIgMi41NjY0IDUuMjQ2MSAzLjg3NSA4LjM0NzcgMy44NzUgMi40OTIyIDAgNS0wLjg0Mzc1IDcuMDQ2OS0yLjU3ODFsMjUuODg3LTIxLjg2M3Y4Mi4xMjVjMCA2LjAzMTIgNC44OTQ1IDEwLjkzIDEwLjkzIDEwLjkzIDYuMDMxMiAwIDEwLjkzLTQuODk0NSAxMC45My0xMC45M2wwLjAwMzkwNy04Mi4xMTcgMjUuODg3IDIxLjg2M2MyLjA0NjkgMS43MzQ0IDQuNTU0NyAyLjU3ODEgNy4wNDY5IDIuNTc4MSAzLjEwOTQgMCA2LjE5OTItMS4zMjAzIDguMzQ3Ny0zLjg3NSAzLjg5ODQtNC42MTMzIDMuMzE2NC0xMS41MDQtMS4yOTY5LTE1LjM5NXoiLz4KIDwvZz4KPC9zdmc+Cg==">
        </div> -->
            <div class="product-list__location">
                <label for="location">Product Location</label>
                <select name="location" id="location" v-model="location">
                    <option value="Auckland">Auckland</option>
                    <option value="Hamilton">Hamilton</option>
                    <option value="Wellington">Wellington</option>
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
            location: null,
        };
    },
    methods: {
        async submitForm() {
            console.log("submit form");
            const response = await fetch("http://localhost:3000/products", {
                method: "POST",
                headers: { "content-type": "application/json" },
                body: JSON.stringify({
                    name: this.name,
                    brand: this.brand,
                    price: this.price,
                    description: this.description,
                    location: this.location,
                })
            });
            const data = await response.json();
            const savedItemId = data._id;
            this.$router.push({ name: 'product', params: { id: savedItemId } });
        },
    }
}
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