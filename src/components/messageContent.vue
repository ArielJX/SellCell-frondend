<template>
    <div class="message-box">
        <p class="name">{{ messageData.username }}</p>
        <p class="message">{{ messageData.message }}</p>
    </div>
</template>

<script>
export default {
    props: {
        messageData: Object,
    },
    data() {
        return {
            username: this.messageData.username,
            message: this.messageData.message
        }
    },
}
</script>

<style lang="scss" scoped>
.message-box {
    display: flex;
}

.name {
    margin-right: 2em;
    font-weight: bold;
    font-size: 20px;
}

.message {
    box-shadow: 2px 3px 10px 2px #ccc;
    padding: 12px;
    border-radius: 30px;
}

p {
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
}
</style>

