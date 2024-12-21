<template>
    <div>
    <form @submit.prevent="registerUser">
      <input v-model="firstname" placeholder="firstname">
      <input v-model="username" placeholder="user">
      <input v-model="password" placeholder="password">
      <button type="submit">Submit</button>
    </form>
      <h3>users:</h3>
      <li id="pAnswer" v-for="(item, index) in userPassSubmited" :key="index">{{ item }}</li>
      <button @click="clearLocal">clear</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        firstname: '',
        username: '',
        password: '',
        userPassSubmited: JSON.parse(localStorage.getItem('submittedAnswers')) || []
      }
    },
    methods: {
      clearLocal() {
        localStorage.clear();
      },
      registerUser() {
        if (this.username.trim() && this.password.trim()) {
          const user = {
            firstname: this.firstname,
            username: this.username,
            password: this.password
          };
          this.userPassSubmited.push(user);
          localStorage.setItem('submittedAnswers', JSON.stringify(this.userPassSubmited));
          this.firstname = '';
          this.username = '';
          this.password = '';
        } else {
          alert('Please fill the form');
        }
      }
    }
  }
  </script>
  
  
  
  <style scoped>
    input {
      margin-top: 4%;
    }
    div {
      border: dashed black 1px;
      border-radius: 10px;
      padding: 0 20px 20px 20px;
      margin-top: 20px;
      display: inline-block;
    }
    button {
      margin: 10px;
    }
    label {
      display: block;
      width: 80px;
      padding: 5px;
    }
    label:hover {
      cursor: pointer;
      background-color: rgb(211, 244, 211);
      border-radius: 5px;
    }
    #pAnswer {
      border-radius: 5px;
      background-color: #141414;
      padding: 5px;
    }
  </style>
  