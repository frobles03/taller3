<template>
  <div class="Trabajo">

    <h1>bienvenido al taller 3 </h1>

    <h1></h1>
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


      <h1>reviews:</h1>
      <hr>
      <div v-for="rev in review" v-bind:key="rev._id">
        <reviewComponent :review="rev" />

      </div>

      <div>


      </div>

      <div>
        <!-- <label for="review">Deja tu review:</label><br>
        <input id="name" type="text" v-model="a" required /> -->
        <form class="d-flex flex-column gap-2" id="formReview" @submit.prevent="reviewPost()">
          <label for="review">Deja tu Review</label>
          <textarea id="review" v-model="msg"></textarea>
          <button type="submit">Enviar review</button>
        </form>



      </div>


    </div>
  </div>
</template>


<script>
// @ is an alias to /src    lista de los trabajos y que si se apreta uno de esos traabajos ver que aplicantes 
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
import reviewComponent from '@/components/HelloWorld.vue'

export default {

  name: 'HomeView',
  data() {
    return {
      review: null,
      text: '',
      msg: ''

    }
  },

  components: {
    reviewComponent
  },

  methods: {
    reviewPost() {
    //   axios.post('//170.239.85.65:4000/products/' ++ '/reviews', JSON.stringify(vue.review),
    //  { headers: { apikey: '549a1f20-84aa-41a5-ad24-13ac557617e65' } })

      axios.post("http://170.239.85.65:4000/products/" +  this.$route.params.id + "/reviews", 
      JSON.stringify({
        review: this.msg,
                // user: { 
                //     name:'Fernando Robles',
                //     email: 'f.robles03@ufromail.cl'



                // }
                
      }),
        {
          headers: {
            apikey: "549a1f20-84aa-41a5-ad24-13ac557617e65",
            "Content-Type": "application/json"
          }
        })
        .then(window.location.reload())
        .catch(err => {
          console.log(err)
        })
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
