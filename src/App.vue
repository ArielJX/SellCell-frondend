<script>
  import { RouterLink, RouterView } from 'vue-router'
  export default {
    data() {
        return {
          LoggedIn: false,
          LoggedOut: true
            };
},
methods: {
        isUserLoggedIn() {
          if (localStorage.getItem('token') != null) {
          this.LoggedIn = true,
          this.LoggedOut = false
        } 
            },
        isUserLoggedOut() {
          localStorage.clear();
          this.LoggedIn= false,
          this.LoggedOut = true
        }
            },
            created() {
            this.isUserLoggedIn,
            this.isUserLoggedOut
          }
          }
  </script>
  
  <template>
    <div class="page-container">
      <div class="content-wrap">
    <header>
      <nav>
        <a href="/"><img src="../src/image/logo.png" alt="logo"></a>
        <div class="nav-link">
          <RouterLink v-if="!LoggedIn, LoggedOut" to="/">Home</RouterLink>
          <RouterLink v-if="!LoggedIn, LoggedOut" to="/login">Login</RouterLink>
          <RouterLink v-if="LoggedIn" to="/profile/:id">Profile</RouterLink>              
          <RouterLink v-if="!LoggedOut, LoggedIn" to="/">Log out</RouterLink>       
        </div>
      </nav>
      <hr>
  
    </header>
  
    <RouterView @UserLoggedIn="isUserLoggedIn" @UserLoggedOut="isUserLoggedOut" />
  
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


  