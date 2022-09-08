<template>
  <header>

  </header>

  <div class="signup-form">
    <h3 class="center">Create a personal account</h3>
    <div class="img-wrapper center">
      <img class="signup-img" src="../image/uploaded-icon.png" alt="">

    </div>
    <span class="center">Upload
      profile photo</span>
    <div class="signup-box center">
      <div class="signup-box--info">
        <p>User Name</p>
        <input type="text">
      </div>
      <div class="signup-box--info">
        <p>Email</p>
        <input type="text">
      </div>
      <div class="signup-box--info">
        <p>Password</p>
        <input type="text">
      </div>
      <div class="signup-box--info">
        <p>Confirm Password</p>
        <input type="text">
      </div>
    </div>
    <button class="mt-1 center" type="button">Create</button>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.signup-form {
  margin: 0 auto;
  width: 60%;
  max-width: 1120px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.img-wrapper {
  width: 220px;
  height: 220px;
}

.center {
  align-self: center;
}

.mt-1 {
  margin-top: 16px;
}

img {
  width: 100%;
}

.signup-box {
  width: 500px;
}

.signup-box--info {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
</style>
