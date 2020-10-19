<template>
  <div class="container">
    {{ email }} {{ password }}
    <h1>Login</h1>
    <div class="columns is-centered card mt-6">
      <div class="column is-three-fifths">
        <b-field label="Email">
          <b-input v-model="email" type="email"> </b-input>
        </b-field>

        <b-field label="Password">
          <b-input v-model="password" type="password"></b-input>
        </b-field>

        <b-button type="button is-dark" expanded @click="login()">Login</b-button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
axios.defaults.withCredentials = true;
export default {
  data() {
    return {
      email: '',
      password: '',
      url: 'https://api.tea-ana.com/v1/auth',
    };
  },
  methods: {
    login: async function() {
      try {
        const res = await axios.post(
          this.url + '/login',

          {
            email: this.email,
            password: this.password,
          },
          { withCredentials: true }
        );

        console.log(res);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
