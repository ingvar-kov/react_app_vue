<template>
    <div className="user">
        <button @click="delete_user(index)">Удалить</button>
        <h3>{{ user.name }}</h3>
        <p>{{ user.mail }} - <b>{{ user.pass }}</b></p>
        <p>New user added</p>
    </div>
</template>

<script>
    export default {
        props: {
            delete_user: {
                type: Function,
                required: true
            },
            user: {
                type: Object,
                required: true
            },
            index: {
                type: Number,
                required: true
            }
        }
    }
</script>

<style scoped>
    button {
        border: none;
        margin-top: 10px;
        margin-right: 10px;
        padding: 10px;
        border-radius: 5px;
        background-color: rgb(255, 218, 218);
        color: rgb(85, 85, 85);
        font-weight: bold;
        cursor: pointer;
        float: right;
        transition: 500ms ease;
    }
    button:hover {
        transform: translateY(3px);
        background-color: rgb(255, 123, 16);
    }
</style>