<template>
  <div class="Trabajo">
    <h1>bienvenido al taller 3 </h1>

    <h1>|°|</h1>
    <div class="post" v-if="review">


      <p>
        <strong>Nombre:</strong> {{ review[0].productId.name }}
      </p>
      
        <strong>imagenes:</strong>
        <li>
          <div v-for="(images) in review[0].productId.images" v-bind:key="images">

            <img :src="images" />
          </div>
        </li>
      


      <p>
        <strong>fecha de creacion:</strong> {{ review[0].productId.createdAt }}
      </p>

      <p>
        <strong>descripcion del producto:</strong> {{ review[0].productId.description }}
      </p>
      
      <div v-for="rev in review" v-bind:key="rev._id">
        
        <strong>review:</strong> {{ rev.review}}
      </div>

      







    </div>
  </div>
</template>

<script>
// @ is an alias to /src    lista de los trabajos y que si se apreta uno de esos traabajos ver que aplicantes 
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'HomeView',
  data() {
    return {
      review: null


    }
  },


  mounted() {
    let vue = this;
    axios.get('//170.239.85.65:4000/products/' + this.$route.params.id + '/reviews')
      .then(function (response) {
        vue.review = response.data;
        console.log(vue.review)
      })




  }
}
</script>
