<script>
import ListItemHome from '../../components/listItemHome.vue';
export default {
  components: { ListItemHome },
  data() {
    return {
      name: null,
      brand: null,
      price: null,
      description: null,
      location: null,
      productDataArray: [],
    }
  },
  methods: {
    async getPost() {
      const response = await fetch(`http://localhost:3000/products`);
      const data = await response.json();
      this.productDataArray = data;
    },
  },
  mounted() {
    this.getPost();
  }
}
</script>

  
<template>
  <main>
    <div class="header-container">
      <div class="header-container__left">
        <div class="content-box">
          <h1 class="header-headline">Find A <span class="text-main-blue"> Perfect Phone</span> For <br> Yourself With
            SellCell.</h1>
          <p>Where you can safely buy and sell your mobile devices.</p>
          <button class="btn__sign-up">
            <span>Sign Up
              Now</span>
          </button>
        </div>

      </div>
      <div class="header-container__right">
        <!-- <img class="header-banner-image" src="src/img/header-guy.jpeg"> -->
      </div>
    </div>
    <section class="search-bar">
      <div class="search-bar__brand">
        <select>
          <option value="" disabled selected>Brand</option>
          <option value="1">Iphone</option>
          <option value="2">Samsung</option>
          <option value="3">Huawei</option>
          <option value="4">Other</option>
        </select>
      </div>
      <div class="search-bar__price">
        <select>
          <option value="" disabled selected>Price</option>
          <option value="1">$400 - $699</option>
          <option value="2">$700 - $999</option>
          <option value="3">$1000 - $1299</option>
          <option value="4">$1300 +</option>
        </select>
      </div>
      <div class="search-bar__location">
        <select>
          <option value="" disabled selected>Location</option>
          <option value="1">Auckland</option>
          <option value="2">Wellington</option>
          <option value="3">Hamilton</option>
          <option value="4">Christchurch</option>
          <option value="5">Other</option>
        </select>
      </div>
      <button class="btn__search">Search My Phone</button>
    </section>

    <section class="mobile-listings">
      <h2>Mobile Listings</h2>
      <p>Shop our unique range of mobile phones, all authenticated by our CellSell experts</p>
      <div class="list-product-page column-3">
        <listItemHome v-for="product of productDataArray" :key="product.id" :product-data="product" />
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
      <!-- <img src="src/img/strip-marketplace.png"> -->
    </div>

    <div class="strip-banner__mobile-brands">
      <div class="container__mobile-brands">
        <h2>Mobile Brands</h2>
        <p>Full range of mobile phones to suit your preference and taste.</p>
      </div>
      <div class="container__mobile-brands-gridbox">
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

    <div class="strip-banner">
      <div class="strip-banner-left">
        <h2>Get your phones checked by our <span class="text-main-blue">Mobile Experts</span></h2>
        <p>Participate in making NZ Green by selling your preloved devices</p>
        <button class="btn"><span>See The Process</span></button>
      </div>
      <div class="strip-banner-right">
        <div class="image-wrapper"></div>
        <!-- <img src="src/img/strip-experts.png" alt=""> -->
      </div>

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
  padding: .8rem 2rem;
  background: $dark-blue;
  color: $white;
  cursor: pointer;
  font-size: 1rem;
  border-radius: .3rem;
  font-weight: 500;
  text-align: center;

  // @media (max-width: 700px) {
  //   font-size: 12px;
  //   padding: 8px 1em;
  //   border-radius: 5px;
  // }

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
    background-image: url(../img/header-guy.jpeg);
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

  .btn__search {
    @include btn-theme
  }

  .search-bar__brand,
  .search-bar__price,
  .search-bar__location {
    padding: 1rem;

    select {
      text-decoration: none;
      display: inline-block;
      padding: 10px;
    }
  }
}

.mobile-listings {
  padding: 4rem;

  .list-product-page {
    padding-top: 15px;
  }

  .column-3 {
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
    background-image: url(../img/strip-marketplace.png);
    background-repeat: none;
    background-size: cover;
    background-position: center;

    .image-wrapper {
      width: 100%;
      height: 100%;
      background-image: url(../img/strip-experts.png);
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

    .mobile-brands-detail {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      border-radius: .5rem;

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
}
</style>