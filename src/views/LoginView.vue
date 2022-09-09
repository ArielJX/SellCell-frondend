<template>
    <div class="login-form">
        <h3 class="center">Log In</h3>

        <div class="login-box center">
            <div class="login-box--info">
                <p>User Name</p>
                <input type="text">
            </div>
            <div class="login-box--info">
                <p>Password</p>
                <input type="text">
            </div>
            <div class="info">
                <span>Don't have an account?</span>
                <a href="../signup">
                    Sign up
                </a>
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
.login-form {
    margin: 0 auto;
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
    margin-top: 16px;
}

.login-box {
    width: 300px;
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

span,
a {
    margin: 8px;
}

button {
    color: white;
    background-color: #1950DA;
    border: none;
    border-radius: 4px;
    padding: 0.5em 2em;
}
</style>