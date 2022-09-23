<template>
  <main>
    <!-- Heading  -->
    <div class="header-container">
      <div class="header-container__left">
        <div class="content-box">
          <h1 class="header-headline">Find A <span class="text-main-blue"> Perfect Phone</span> For <br> Yourself With
            SellCell.</h1>
          <p>Where you can safely buy and sell your mobile devices.</p>
          <button @click="$router.push('signup')" class="btn__sign-up" type="button">
            <span>Sign Up
              Now</span>
          </button>
        </div>

      </div>
      <div class="header-container__right">

      </div>
    </div>
    <section class="search-bar">
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
        <select v-model="price">
          <option disabled selected>Price</option>
          <option>below $500</option>
          <option>$500 - $1000</option>
          <option>$1000 - $2000</option>
          <option>Above $2000</option>
        </select>
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
      <button @click="findproductLists" class="btn__search"><span>Search My Phone</span></button>
    </section>


    <!--All Mobile listings & Searched Mobile listings -->
    <section class="mobile-listings">
      <h2>Mobile Listings found</h2>
      <p>Shop our unique range of mobile phones, all authenticated by our CellSell experts</p>

      <div class="list-product-page columns">
        <listItemHome v-if="!showing" v-for="product of productArray" :key="product._id" :product-data="product" />
        <searchedProduct v-else v-for="findproduct of findproductArray" :key="findproduct._id" :findproduct-data="findproduct" />
      </div>
    </section>

    <div class="strip-banner">
      <div class="strip-banner-left">
        <h2>New Zealand's Most Trusted, <span class="text-main-blue">Marketplace</span> for selling and buying mobile
          phones.</h2>
        <p>Never worry about engaging with scammers, Never worry about buying fake, authentic mobile phones.</p>
        <button class="btn"><span>See The Process</span></button>
      </div>
      <div class="strip-banner-right"></div>

    </div>

    <div class="strip-banner__mobile-brands">
      <div class="container__mobile-brands">
        <h2>Mobile Brands</h2>
        <p>Full range of mobile phones to suit your preference and taste.</p>
      </div>
      <div class="container__mobile-brands-gridbox">
        <div class="mobile-brands-detail">
          <div class="mobile-brands-image">
            <img src="src/image/apple.png">
          </div>
          <p>Apple</p>
        </div>
        <div class="mobile-brands-detail">
          <div class="mobile-brands-image">
            <img src="src/image/samsung.png">
          </div>
          <p>Samsung</p>
        </div>

        <div class="mobile-brands-detail">
          <div class="mobile-brands-image">
            <img src="src/image/huawei.png">
          </div>
          <p>Huawei</p>
        </div>

        <div class="mobile-brands-detail">
          <p>+ View More</p>
        </div>
      </div>
    </div>

    <div class="strip-banner">
      <div class="strip-banner-left">
        <h2>Get your phones checked by our <span class="text-main-blue">Mobile Experts</span></h2>
        <p>Participate in making NZ Green by selling your preloved devices</p>
        <button class="btn"><span>See The Process</span></button>
      </div>
      <div class="strip-banner-right">
        <div class="image-wrapper"></div>

      </div>

    </div>
  </main>
</template>



<script>
import listItemHome from '../components/listItemHome.vue';
import searchedProduct from '../components/searchedProduct.vue';

export default {
  components: { listItemHome, searchedProduct },
  data() {
    return {
      brand: null,
      price: null,
      location: null,
      productArray: [],
      findproductArray: [],
      showing: false
    };
  },

  methods: {
    async getItem() {
      const response = await fetch(`http://localhost:3000/products`);
      const data = await response.json();
      this.productArray = data;
    },

    async findproductLists() {
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
      this.showing = true;
    },

  },
  mounted() {
    this.getItem()
  }
}
</script>


<style lang="scss">
$main-blue: #184DD1;
$dark-blue: #003489;
$background-blue: #E1EDFF;
$black: black;
$white: white;

@mixin btn-theme {
  display: inline-block;
  justify-content: center;
  padding: .8rem 2rem;
  background: $dark-blue;
  color: $white;
  cursor: pointer;
  font-size: 1rem;
  border-radius: .3rem;
  font-weight: 500;
  text-align: center;

  &:hover {
    background: $main-blue;
  }
}

@mixin strip-banner-theme {
  background-color: $background-blue;
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin: 0 auto 0 auto;

  .container {
    padding-right: 15px;
  }

  h1 {
    margin: 0;
  }

  p {
    margin-right: 15px;
  }

  .btn {
    @include btn-theme;
  }
}

h1,
h2 {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

p {
  font-family: sans-serif;
}

span {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

.text-main-blue {
  color: $main-blue;
}

.header-container {
  width: 100%;
  height: 400px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;

  .header-container__left {
    width: 100%;

    .content-box {
      padding: 4em;

      h1,
      p {
        margin-bottom: 2rem;
      }
    }
  }

  &__right {
    width: 100%;
    height: 100%;
    background-image: url(../image/header-guy.jpeg);
    background-repeat: none;
    background-size: cover;
    background-position: center;
  }

  .btn__sign-up {
    @include btn-theme
  }
}


.search-bar {
  width: 100%;
  height: 6rem;
  background-color: $main-blue;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  padding: 1rem 0;

  .btn__search {
    margin-left: 2em;
    @include btn-theme
  }

  .search-bar__brand,
  .search-bar__price,
  .search-bar__location {
    padding-right: 1rem;

    select {
      text-decoration: none;
      display: inline-block;
      padding: 10px;
    }

    label {
      font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
      color: white;
      margin-right: 6px;
    }
  }
}

.mobile-listings {
  padding: 4rem;

  .list-product-page {
    padding-top: 15px;
  }

  .columns {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    gap: 2em;
  }

  .btn__view-listing {
    @include btn-theme;
  }
}

.strip-banner {
  background-color: $background-blue;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 300px;
  margin: 4rem 0 0 0;

  &-left {
    width: 100%;
    padding: 2rem 4rem;
    margin: 0 auto;
  }

  &-right {
    width: 100%;
    height: 100%;
    background-image: url(../image/strip-marketplace.png);
    background-repeat: none;
    background-size: cover;
    background-position: center;

    .image-wrapper {
      width: 100%;
      height: 100%;
      background-image: url(../image/strip-experts.png);
      background-repeat: none;
      background-size: cover;
      background-position: center;
    }
  }

  h1 {
    margin: 0;
  }

  p {
    margin-right: 15px;
  }

  .btn {
    @include btn-theme;
  }
}

.strip-banner__mobile-brands {
  background-color: white;
  margin: 4rem auto;
  width: 100%;

  h2,
  p {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container__mobile-brands-gridbox {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 2rem;
    justify-content: center;
    align-items: center;
    padding: 0 15%;
  }
}

.mobile-brands-detail {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border-radius: .5rem;
  gap: 1.5rem;
  margin-top: 1rem;

  .mobile-brands-image {
    max-width: 80px;
    width: 80%;
    height: auto;

    img {
      object-fit: contain;
      width: 100%;
      height: 100%;
    }
  }
}

@media (max-width: 700px) {

  .header-container {
    height: 600px;
    position: relative;

    &__left {
      position: absolute;

      .content-box {
        padding: 1em;

        h1,
        p,
        .text-main-blue {
          color: white;
        }

        .text-main-blue {
          font-size: 46px;
        }
      }
    }
  }

  .search-bar {

    .search-bar__brand,
    .search-bar__price,
    .search-bar__location {
      padding: 8px;

      select {
        padding: 6px;
      }
    }
  }

  .strip-banner {
    &-right {
      display: none;
    }
  }

  p {
    font-size: 12px;
  }
}
</style>