<template>
<nav class="navbar navbar-expand-lg bg-body-tertiary">
  <div class="container-fluid">
    <router-link class="navbar-brand" :to="{ path:'/'}">Super Store</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item"> <router-link class="nav-link active" to="/">Home</router-link> </li>
        <li class="nav-item"> <router-link class="nav-link" to="/about">About</router-link> </li>
        <li class="nav-item"> <router-link class="nav-link" to="/contact">Contact</router-link> </li>
        <!-- <li class="nav-item"> <router-link class="nav-link" to="/product">Products</router-link> </li> -->
      </ul>
      <form @submit.prevent="search" class="d-flex" role="search">
        <input  class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="keyword" >
        <button  class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
</template>

<script>
import axios from 'axios';
  export default {
    data(){
      return {
        keyword : ''
      }
    },
    
    methods: {
      search() {
        var self =this;
        const lowercaseKeyword = typeof this.keyword === 'string' ? this.keyword.toLocaleLowerCase() : '';
        
        axios.get('http://localhost:3000/search/' + lowercaseKeyword).then(response => {
          self.$store.commit('setProduct', response.data) 
        });
      }
    }
  }
</script>

<style scoped>

</style>