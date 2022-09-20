
<script>
import ListItemHome from '../../components/listItemHome.vue';
import searchedProduct from '../../components/searchedProduct.vue';
export default {
  components: { ListItemHome, searchedProduct },
  data() {
    return {
      name: null,
      brand: null,
      price: null,
      description: null,
      location: null,
      productDataArray: [],
      findproductArray: []
    }
  },
  methods: {
    async getPost() {
      const response = await fetch(`http://localhost:3000/products`);
      const data = await response.json();
      this.productDataArray = data;
    },

    async findproductLists() {
      console.log("filtered products");
      const response = await fetch("http://localhost:3000/findproducts", {
        method: "POST",
        headers: { "content-type": "application/json" },
        body: JSON.stringify({
          brand: this.brand,
          price: this.price,
          location: this.location
        })
      })
      const data = await response.json();
      this.findproductArray = data;
      this.$router.push({ name: 'home' });
    },
  },
  mounted() {
    this.getPost();
  }
}
</script>

  

<template>
  <main>
    <!-- Heading  -->
    <div class="header-container">
      <div class="header-container__left">
        <h1 class="header-headline">Find A <span class="text-main-blue"> Perfect Phone</span> For <br> Yourself With
          SellCell.</h1> <br>
        <p>Where you can safely buy and sell your mobile devices.</p> <br><br> <button @click="$router.push('signup')"
          class="btn__sign-up" type="button">Sign Up
          Now</button>
      </div>
      <div class="header-container__right">
        <img class="header-banner-image" src="src/img/header-guy.jpeg">
      </div>
    </div>



    <!-- Search bar -->
    <section class="search-bar">
      <div class="search-bar__container">
        <!-- <div class="search-bar__keywords">
          <input type="text" placeholder="Search Keyword" v-model="name">
        </div> -->
      </div>

      <div class="search-bar__brand">
        <label>Brand</label>
        <select v-model="brand">
          <option disabled selected>Brand</option>
          <option>Apple</option>
          <option>Oppo</option>
          <option>Samsung</option>
          <option>Huawei</option>
          <option>Other</option>
        </select>
      </div>
      <div class="search-bar__price">
        <label>Price</label>
        <input type="number" v-model="price">
      </div>
      <div class="search-bar__location">
        <label>Location</label>
        <select v-model="location">
          <option disabled selected>Location</option>
          <option>Auckland</option>
          <option>Wellington</option>
          <option>Hamilton</option>
          <option>Christchurch</option>
          <option>Other</option>
        </select>
      </div>
      <button @click="findproductLists" class="btn__search">Search My Phone</button>
    </section>


    <!-- All Mobile listings -->




    <!--Searched Mobile listings -->
    <section class="mobile-listings">
      <h2>Mobile Listings found</h2>
      <p>Shop our unique range of mobile phones, all authenticated by our CellSell experts</p>

      <div class="list-product-page">
        <listItemHome v-for="product of productDataArray" :key="product.id" :product-data="product" />
        <searchedProduct v-for="findproduct of findproductArray" :findproduct-data="findproduct" />
      </div>
    </section>


    <!-- Marketplace banner -->
    <div class="strip-banner__marketplace">
      <div class="container__marketplace">
        <h2>New Zealand's Most Trusted, <span class="text-main-blue">Marketplace</span> for selling and buying mobile
          phones.</h2>
        <br>
        <p>Never worry about engaging with scammers, Never worry about buying fake, authentic mobile phones.</p>
        <br> <br>
        <button class="btn__marketplace">See The Process</button>
      </div>
      <img src="src/img/strip-marketplace.png">
    </div>

    <div class="strip-banner__mobile-brands">
      <div class="container__mobile-brands">
        <h2>Mobile Brands</h2>
        <p>Full range of mobile phones to suit your preference and taste.</p>
      </div>
      <div class="container__mobile-brands-flexbox">
        <div class="mobile-brands-detail">
          <div class="mobile-brands-image">
            <img src="src/img/apple.png">
          </div>
          <p>Apple</p>
        </div>

        <div class="mobile-brands-detail">
          <div class="mobile-brands-image">
            <img src="src/img/samsung.png">
          </div>
          <p>Samsung</p>
        </div>

        <div class="mobile-brands-detail">
          <div class="mobile-brands-image">
            <img src="src/img/huawei.png">
          </div>
          <p>Huawei</p>
        </div>

        <div class="mobile-brands-detail">
          <p>+ View More</p>
        </div>
      </div>
    </div>


    <!-- Mobile expert banner -->
    <div class="strip-banner__mobile-experts">
      <div class="container__mobile-experts">
        <h2>Get your phones checked by our <span class="text-main-blue">Mobile Experts</span></h2>
        <br>
        <p>Participate in making NZ Green by selling your preloved devices</p>
        <br> <br>
        <button class="btn__mobile-experts">See The Process</button>
      </div>
      <img src="src/img/strip-experts.png" alt="">
    </div>
  </main>
</template>



<style lang="scss">
$main-blue: #184DD1;
$dark-blue: #003489;
$background-blue: #E1EDFF;
$black: black;
$white: white;

@mixin btn-theme {
  display: inline-block;
  justify-content: center;
  margin-top: 1rem;
  padding: 15px 1em;
  background: $dark-blue;
  color: $white;
  cursor: pointer;
  border-radius: .3rem;
  text-align: center;
  font-size: 16px;
  border: none;
  border: 1px solid white;

  &:hover {
    background: $main-blue;
  }
}

@mixin strip-banner-theme {
  background-color: $background-blue;
  display: flex;
  justify-content: space-between;
  padding: 100px;
  width: 100%;
  margin: 0 auto 0 auto;

  .container__marketplace {
    padding-right: 15px;
  }

  img {
    height: 300px;
  }

  h1 {
    margin: 0;
  }

  p {
    margin-right: 15px;
  }

  .btn__marketplace {
    @include btn-theme;
  }
}

.text-main-blue {
  color: $main-blue;
}

li {
  list-style-type: none;
  margin-right: 2em;
}


.header-container {
  display: flex;
  align-items: center;
  justify-content: space-between;

  &__left {
    width: 600px;
    padding-left: 6em;
  }

  &__right {
    width: 600px;
    height: 400px;

    img {
      width: 600px;
      height: 400px;
    }
  }

  .btn__sign-up {
    @include btn-theme
  }
}

.search-bar {
  padding: 20px;
  width: 100%;
  height: 10rem;
  background-color: $main-blue;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;

  .btn__search {
    margin-left: 2em;
    @include btn-theme
  }

  .search-bar__keywords {
    width: 100%;

    input {
      width: 90%;
      display: inline-block;
      padding: 10px;
    }
  }

  .search-bar__brand,
  .search-bar__price,
  .search-bar__location {
    padding: 20px;
    display: block;
    color: white;

    label {
      margin-right: 1em;
    }

    select {
      text-decoration: none;
      display: inline-block;
      padding: 10px;
      width: 150px;
    }

    input {
      display: inline-block;
      padding: 10px;
      width: 120px;
    }
  }
}

.mobile-listings {
  padding-top: 30px;
  padding-bottom: 30px;

  h2,
  p {
    padding-bottom: 15px;
  }

  .list-product-page {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(4, minmax(100px, 1fr));
    grid-gap: 20px;
    padding: 50px
  }

  .btn__view-listing {
    @include btn-theme;
  }
}

.strip-banner__marketplace {
  background-color: $background-blue;
  display: flex;
  justify-content: space-between;
  padding: 100px;
  width: 100%;
  margin: 0 auto 0 auto;

  .container__marketplace {
    padding-right: 15px;
  }

  img {
    height: 300px;
  }

  h1 {
    margin: 0;
  }

  p {
    margin-right: 15px;
  }

  .btn__marketplace {
    @include btn-theme;
  }
}

.strip-banner__mobile-brands {
  background-color: white;
  padding: 100px;
  width: 100%;
  margin: 0 auto 0 auto;

  h2,
  p {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container__mobile-brands-flexbox {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 2em;
    padding: 5em;
    flex: 1 0 0;
    justify-content: center;
    align-items: center;

    .mobile-brands-detail {
      display: block;
      border-radius: .5rem;
      padding: 3rem;
      gap: 1.5rem;

      .mobile-brands-image {
        display: block;
        width: 100%;
        height: 150px;
        padding: 1rem;

        img {
          object-fit: contain;
          width: 100%;
          height: 100%;
        }
      }
    }
  }
}

.strip-banner__mobile-experts {
  background-color: $background-blue;
  display: flex;
  justify-content: space-between;
  padding: 100px;
  width: 100%;
  margin: 0 auto 0 auto;

  .container__mobile-experts {
    padding-right: 15px;
  }

  img {
    height: 300px;
  }

  h1 {
    margin: 0;
  }

  p {
    margin-right: 15px;
  }

  .btn__mobile-experts {
    @include btn-theme;
  }
}
</style>