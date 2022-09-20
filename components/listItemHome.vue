    <template>
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
            </div>
            <div class="subtitle-container">
            <h5>$ {{productData.price}}</h5>
            </div>
            <div class="subtitle-container">
            <button @click="$router.push(`/product/${productData._id}`)" id="profile-view-button" class="blue-button"
                type="button">View</button>
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
    .item-box {
    min-width: 190px;
    max-width: 220px;
    display: block;
    border: 1px solid gainsboro;
    border-radius: 6px;
    padding-bottom: 1em;
    }

    img {
    width: 100%;
    border-radius: 3px;
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