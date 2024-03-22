<template>
<div>
    <h5>Login </h5>
    <button class="btn btn-primary" @click="handleLogin">Continue</button>
</div>
</template>

<script>
export default {
  methods: {
    handleLogin() {
     + localStorage.setItem("token", "12345");
      this.$router.push("/");
    },
  },
};
</script>