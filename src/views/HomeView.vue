<script>
  import ListItemHome from '../../components/listItemHome.vue';
    export default{

    }
</script>

  
<template>
  <main>
    <div class="header-container">
      <div class="header-container__left">
        <h1 class="header-headline">Find A <span class="text-main-blue"> Perfect Phone</span> For <br> Yourself With
          SellCell.</h1> <br>
        <p>Where you can safely buy and sell your mobile devices.</p> <br><br> <button class="btn__sign-up">Sign Up
          Now</button>
      </div>
      <div class="header-container__right">
        <img class="header-banner-image" src="src/img/header-guy.jpeg">
      </div>
    </div>
    <section class="search-bar">
      <div class="search-bar__container">
        <div class="search-bar__keywords">
          <input type="text" placeholder="Search Keyword">
        </div>
      </div>
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
      <div class="list-product-page">
        <div class="listing-box column-3">
          <div class="item-box">
              <div>
                  <img src="../image/iphone13.png" alt="">
              </div>
              <div class="subtitle-container">
                  <span>Auckland</span>
                  <span>Listed: Thur, 1 Sep</span>
              </div>
              <div class="subtitle-container mb-2">
                  <h4>Iphone 13 pro, 99% new</h4>
              </div>
              <div class="subtitle-container underline">
                  <p class="font-blue">48 Watchers</p>
                  <p>Price by negotiation</p>
              </div>
              <div class="subtitle-container">
                  <button id="profile-view-button" class="blue-button" type="button" @click="$router.push('product')">View</button>
                  <button id="profile-delete-button" class="white-button" type="button">Delete</button>
              </div>
          </div>
        </div>  
        <button class="btn__view-listing">Browse More Phones</button>
      </div>
    </section>

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
  padding: .8rem 3rem;
  background: $dark-blue;
  color: $white;
  cursor: pointer;
  font-size: 1.7rem;
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
    select {
      text-decoration: none;
      display: inline-block;
      padding: 10px;
    }
  }
}
.mobile-listings {
  padding-top: 30px;
  padding-bottom: 30px;
  h2,
  p {
    padding-left: 100px;
  }
  p {
    padding-bottom: 15px;
  }
  .list-product-page {
    box-sizing: border-box;
    width: 100%;
    border: solid #5B6DCD 5px;
    height: 500px;
    display: flex;
    justify-content: center;
    align-items: center;
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