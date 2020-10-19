<template>
  <div class="container">
    {{ name }} {{ email }} {{ password }}
    <h1>Register</h1>
    <div class="columns is-centered card mt-6">
      <div class="column is-three-fifths">

        <b-field label="Name">
          <b-input v-model="name"></b-input>
        </b-field>

        <b-field label="Email">
          <b-input v-model="email" type="email"></b-input>
        </b-field>

        <b-field label="Password">
          <b-input v-model="password" type="password"></b-input>
        </b-field>

        <b-button type="button is-dark" expanded @click="register()">Register</b-button>

      </div>
    </div>
  </div>
</template>

<script>

import axios from 'axios';
//allows cookies 
axios.defaults.withCredentials = true;

export default {
  data() {
    return {
      name: '',
      email: '',
      password: '',
      url: 'https://api.tea-ana.com/v1/auth',
    };
  },
  methods: {
    register: async function() {
      try {
        const res = await axios.post(this.url + '/register', {
          name: this.name,
          email: this.email,
          password: this.password,
        });

        console.log(res.data);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
