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
    <div className="input">
      <input type="text" v-model="user_name" placeholder="Имя">
      <input type="password" v-model="user_pass" placeholder="Пароль">
      <input type="email" v-model="user_mail" placeholder="E-mail">
    </div>
    <div className="info_block">
      <button @click="send_data()">Отправить</button>
      <p className="error">{{ error }}</p>
    </div>
    <div v-if="users.length == 0" className="user">
      <p>Нет активных пользователей</p>
    </div>
    <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :delete_user="delete_user"/>
    <img src="./images/21.png" className="back_21">
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
    cursor: pointer;
    transition: 100ms;
  }
  input:focus {
    outline: 2px solid rgb(171, 0, 194);
  }
  button {
    display: inline-block;
    margin: 20px;
    padding: 10px;
    color: rgb(43, 43, 43);
    background-color: rgb(99, 255, 146);
    font-weight: 600;
    border-radius: 5px;
    border: none;
    transition: 500ms;
    cursor: pointer;
  }
  button:hover {
    transform: translateY(-3px);
    box-shadow: 0 0 0 2px rgba(98, 0, 238, 0.2);
  }
  .input {
    display: block;
  }
  .info_block {
    display: block;
    margin-bottom: 20px;
  }
  .error {
    margin: 20px;
    display: inline-block;
    font-weight: 700;
  }
  .wrapper {
    position: relative;
    padding: 40px;
    margin: 10px;
    margin-top: 20px;
    background: linear-gradient(45deg, #cefff7, #ba4dec);
    border-radius: 20px;
    background-image: ;
  }
  .user {
    margin: 20px;
    padding: 20px;
    background-color: rgb(255, 255, 255);
    border-radius: 5px;
    border: none;
    display: inline-block;
    width: 20%;
  }
  .user p {
    color: rgb(117, 117, 117);
  }
  .back_21 {
    position: absolute;
    width: 25vh;
    top: 20px;
    right: 20px;
  }
</style>
