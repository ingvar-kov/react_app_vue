<script>
  import User from './components/User.vue'

  export default {
    components: { User },
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
      },
      delete_user(index) {
        this.users.splice(index, 1);
      }
    }
  }
</script>

<template>
  <div className="wrapper">
    <input type="text" v-model="user_name" placeholder="Имя">
    <input type="password" v-model="user_pass" placeholder="Пароль">
    <input type="email" v-model="user_mail" placeholder="E-mail">
    <p className="error">{{ error }}</p>
    <button @click="send_data()">Отправить</button>
    <div v-if="users.length == 0" className="user">
      <p>Нет активных пользователей</p>
    </div>
    <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :delete_user="delete_user"/>
  </div>
</template>

<style scoped>
  div {
    margin: 0 auto;
    padding: 0 auto;
  }
  input {
    margin: 20px;
    padding: 10px;
    border-style: none;
    border-radius: 5px;
    border-color: rgb(103, 85, 119);
  }
  button {
    display: block;
    margin: 20px;
    padding: 10px;
    color: rgb(43, 43, 43);
    background-color: rgb(165, 255, 165);
    font-weight: 600;
    border-radius: 5px;
    border: none;
  }
  .wrapper {
    padding: 40px;
    margin: 10px;
    margin-top: 20px;
    background-color: rgb(198, 169, 236);
    border-radius: 20px;
  }
  .user {
    margin: 20px;
    padding: 20px;
    background-color: rgb(227, 205, 255);
    border-radius: 5px;
    border: none;
    display: inline-block;
    width: 20%;
  }
</style>
