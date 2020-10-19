<template>
  <div class="container">
    <div class="card">
      <h1>Profile</h1>
      <div class="card-content" v-if="data!=null">
        <div class="media">
          <div class="media-content">
            <p class="title is-4">Name: {{ data.user.name }}</p>
            <p class="subtitle is-4">Email: {{ data.user.email }}</p>
          </div>
        </div>
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
      data: null,
    };
  },
  methods: {
    getProfile: async function() {
      try {
        const res = await axios.get('https://api.tea-ana.com/v1/auth/profile');
        this.data = res.data;
      } catch (error) {
        console.error(error);
      }
    },
  },
  mounted() {
    this.getProfile();
  },
};
</script>
