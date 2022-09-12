<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>
<template>
  <header>
    <nav>
      <img src="../src/image/logo.png" alt="logo">
      <div class="nav-link">
        <RouterLink to="/home">Home</RouterLink>
        <RouterLink to="/login">Login</RouterLink>
        <RouterLink to="/profile">Profile</RouterLink>
      </div>
    </nav>
  </header>
  <RouterView />

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
</template>

<style scoped>
img {
  width: 200px;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

.nav-link {
  padding-right: 1em;
  font-size: 20px;
}

a {
  text-decoration: none;
  padding: 0 2em;
  color: black;
}

a:hover {
  color: #003489;
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
}

ul {
  display: flex;
  justify-content: space-between;
  width: 70%;
}

li {
  list-style: none;
}

i {
  padding-right: 2em;
}
</style>
