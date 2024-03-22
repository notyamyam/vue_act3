<script>
import { RouterLink, RouterView } from "vue-router";

export default {
  el: "#App",

};
</script>

<template id="App">
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark w-100 p-2">
      <a class="navbar-brand">Cart</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active me-3 ">
            <RouterLink to="/" class="custom-link">Home <span class="sr-only">(current)</span></RouterLink>
          </li>
          <li class="nav-item active">
            <RouterLink to="/login" class="custom-link">Login</RouterLink>
          </li>
        </ul>
      </div>
  </nav>

    <RouterView />
</template>

<style>
  .custom-link {
    color: white;
  }
</style>


