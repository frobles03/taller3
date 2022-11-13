<template>
  <div class="d-flex flex-column align-items-start">
    <h5><Strong>Usuario:</Strong>  <br>{{review.user.name}}</h5>
    <h6><Strong>Review:</Strong> <br>{{review.review}}</h6>
    <hr>
  </div>
</template>

<script>
export default {
    name: "ReviewComponent",
    props: {
        review: Object,
  }
}
</script>

<style>
</style>