<template>
  <div class="Trabajos">
    <h1>bienvenido al taller 3</h1>
    <div class="post" v-for="product in products" v-bind:key="product._id">
      <!-- <strong> <router-link to="/trabajo">{{product.title}}</router-link>  </strong> :{{ product.salary }} -->

      <li>
        
          <strong>nombre del producto: </strong> {{ product.name }}
        

        
          <strong> fecha de creacion</strong> {{ product.createdAt }}
      
      

        <div v-for="(images) in product.images" v-bind:key="images">

          <img :src="images" />
        </div>

      </li>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src    lista de los trabajos y que si se apreta uno de esos traabajos ver que aplicantes 
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'productsView',
  data() {
    return {
      products: []
    }
  },

  mounted() {
    let vue = this;
    axios.get('http://170.239.85.65:4000/products')
      .then(function (response) {
        vue.products = response.data;
        console.log(vue.products)
      })
  }
}
</script>
