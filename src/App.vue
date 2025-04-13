<script>
  export default {
    data() {
      return {
        users: [],
        user_name: '',
        user_pass: '',
        user_mail: ''
      }
    },
    methods: {
      send_data() {
        this.users.push({
          name: this.user_name,
          pass: this.user_pass,
          mail: this.user_mail
        })
      }
    }
  }
</script>

<template>
  <input type="text" v-model="user_name" placeholder="Имя">
  <input type="password" v-model="user_pass" placeholder="Пароль">
  <input type="email" v-model="user_mail" placeholder="E-mail">
  <button @click="send_data()">Отправить</button>
  <p>{{ users }}</p>
</template>

<style scoped>
  input {
    margin: 20px;
    padding: 10px;
    border-radius: 5px;
  }
  button {
    display: block;
    margin: 20px;
    padding: 10px;
    color: rgb(43, 43, 43);
    background-color: rgb(68, 236, 68);
    font-weight: 600;
    border-radius: 5px;
    border: none;
  }
</style>
