<script>
  export default {
    data() {
      return {
        users: [],
        error: '',
        user_name: '',
        user_pass: '',
        user_mail: ''
      }
    },
    methods: {
      send_data() {
        if(this.user_name == '') {
          this.error = 'Заполните поле имя';
          return;
        } else if(this.user_pass == '') {
          this.error = 'Заполните поле пароль';
          return;
        } else if(this.user_mail == '') {
          this.error = 'Заполните поле почта';
          return;
        }
        this.error = '';
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
  <p className="error">{{ error }}</p>
  <button @click="send_data()">Отправить</button>
  <div v-if="users.length == 0" className="user">
    <p>Нет активных пользователей</p>
  </div>
  <div v-for="(el, index) in users" :key="index" className="user">
    <h3>{{ el.name }}</h3>
    <p>New user added</p>
  </div>
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
  .user {
    margin: 10px;
    padding: 20px;
    background-color: rgb(191, 191, 255);
    border-radius: 5px;
    border: none;
    display: inline-block;
    width: 20%;
  }
</style>
