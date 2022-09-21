<template>
    <div class="login-form">
        <h1 class="center">Log In</h1>

        <div class="login-box center">
            <div class="login-box--info">
                <label>User Name</label>
                <input type="text">
            </div>
            <div class="login-box--info">
                <label>Password</label>
                <input type="text">
            </div>
            <div class="info">
                <span>Don't have an account?</span>
                <a href="../signup">
                    Sign up
                </a>
            </div>
        </div>
        <button class="mt-1 center" type="button">Log in</button>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.login-form {
    margin: 8em auto;
    width: 60%;
    max-width: 800px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}


.center {
    align-self: center;
}

.mt-1 {
    margin-top: 2em;
}


label {
    font-family: sans-serif;
    font-size: 20px;
}

input {
    height: 36px;
    width: 400px;
    margin-bottom: 2em;
}

.login-box {
    width: 400px;
    margin-top: 2em;
}

.login-box--info {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
}

.info {
    display: flex;
    flex-direction: row;
    gap: 1em;
}

h1 {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

span,
a {
    margin: 8px 2px;
    font-size: 18px;
    font-family: sans-serif;
}

a:hover {
    color: red;
}

button {
    color: white;
    background-color: #1950DA;
    border: none;
    border-radius: 2px;
    padding: 1em 2em;
    margin-bottom: 4em;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: 16px;
}
</style>