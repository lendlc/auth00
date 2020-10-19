<template>
  <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
  <b-navbar shadow>
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
          alt="Lightweight UI components for Vue.js based on Bulma"
        />
      </b-navbar-item>
    </template>
    <template slot="start">
      <b-navbar-item href="#">
        <strong>
          <router-link to="/">Home</router-link>
        </strong>
      </b-navbar-item>
      <b-navbar-item href="#">
        <strong>
          <router-link to="/profile">Profile</router-link>
        </strong>
      </b-navbar-item>
    </template>

    <template slot="end">
      <b-navbar-item tag="div">
        <div class="buttons">
          <a class="button is-light">
            <strong><router-link to="/register">Register</router-link></strong>
          </a>
          <a class="button is-dark">
            <strong><router-link to="/login">Login</router-link></strong>
          </a>
          <a class="button is-secondary" @click="logout()">
            <!-- removes cookie,  redirects to landing page -->
            <strong><router-link to="/">logout</router-link></strong>
          </a>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>

<script>
import axios from 'axios';
axios.defaults.withCredentials = true;
export default {
  methods: {
    logout: async function() {
      try {
        const res = await axios.get('https://api.tea-ana.com/v1/auth/logout', {
          withCredentials: true,
        });
        console.log(res);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
