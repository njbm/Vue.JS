<template>
  <div id="app"> 
    <Navbar @search="search" :keyword="keyword"/>
    
    <div class="row d">
      <div class="col-sm-9">
        <router-view></router-view>
      </div>
      <div class="col-sm-3">
        <Cart @itemRemoved="removeItem" :items="cart" />
      </div>
    </div>

  </div>
</template>


<script>
import Navbar from './components/Navbar.vue';
import Cart from './components/Cart.vue';
import data from './data'

  export default {
      components: { Navbar,   Cart },
      data(){
        return {
          items:[],cart:[]
        }
      },
      mounted(){
        this.items =data
      }
  }
</script>

<style>
.d{padding: 20px;}
</style>
