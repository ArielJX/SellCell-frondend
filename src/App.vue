<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>
  
<template>
  <div class="page-container">

    <nav>
      <img src="../src/image/logo.png" alt="logo">
      <div id="mobile-nav">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/login">Login</RouterLink>
        <RouterLink to="/profile">Profile</RouterLink>
      </div>
      <a href="javascript:void(0);" class="icon mobile-only" @click="myFunction()">
        <i class="fa fa-bars" style="font-size: 28px;"></i>
      </a>
      <div class="nav-link">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/login">Login</RouterLink>
        <RouterLink to="/profile">Profile</RouterLink>
      </div>
    </nav>

    <div class="content-wrap">
      <RouterView />
    </div>
    <footer>
      <ul>
        <li>© 2022 SellCell Limited</li>
        <li>Contact Us</li>
        <li>About Us</li>
        <li>Terms & Conditions</li>
      </ul>
      <div class="social-media">
        <i class="fa-brands fa-facebook-f"></i>
        <i class="fa-brands fa-instagram"></i>
      </div>
    </footer>
  </div>
</template>
  
<style lang="scss" scoped>
img {
  width: 200px;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  border-bottom: black 1px solid;
  margin-bottom: 1rem;
  overflow: hidden;
  position: relative;

  a {
    color: black;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
    display: block;

    .icon {
      background: black;
      display: block;
      position: absolute;
      right: 0;
      top: 0;
    }
  }

}

.nav-link {
  display: flex;
  flex-direction: row;
  padding-right: 1em;
  font-size: 20px;
}

#mobile-nav {
  display: none;
}

.mobile-only {
  display: none;
}

a {
  text-decoration: none;
  padding: 0 2em;
  color: black;
}

a:hover {
  color: #003489;
}

.page-container {
  position: relative;
  min-height: 100vh;
}

.content-wrap {
  padding-bottom: 4rem;
}

footer {
  height: 80px;
  width: 100%;
  background-color: #13305F;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-size: 18px;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: absolute;
  bottom: 0;
}

ul {
  display: flex;
  // justify-content: space-between;
  gap: 1rem;
  width: 70%;
}

li {
  list-style: none;
  font-size: 12px;
}

.social-media {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  margin: 18px 0;
  padding-inline-end: 40px;
}

@media screen and (max-width: 680px) {
  .nav-link {
    display: none;
  }

  .mobile-only {
    display: inline;
  }
}
</style>

<script>
function myFunction() {
  var x = document.getElementById("mobile-nav");
  if (x.style.display === "block") {
    x.style.display = "none";
  } else {
    x.style.display = "block";
  }
}
</script>
  