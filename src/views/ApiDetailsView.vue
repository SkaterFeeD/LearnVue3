<template>
  <div class="card">
    <div class="card-header">{{product.title}}</div>
    <div class="card-body">
      <img :src="product.thumbnail" :alt="product.title"/>
      <p>Описание товара: {{ product.description }}</p>
    </div>
    <div class="card-footer d-flex justify-content-between" >
      <div class="fw-bold fst-italic">Цена: {{product.price}}$</div>
      <div><RouterLink class="btn btn-dark" to="/api">Назад</RouterLink></div>
    </div>

  </div>
</template>

<style scoped>
  .card {
    width: 500px;
  }
  .card img {
    width: 400px;
    margin: 0 auto;
  }
</style>

<script>
import router from "@/router/index.js";

export default {
  methods: {
    router() {
      return router
    }
  },
  data(){
    return{
      product: null,
    }
  },
  created() {
    const id = this.$route.params.id
    const url ="https://dummyjson.com/products/" + id;
    fetch(url)
        .then(response => response.json())
        .then(data => this.product = data)
    console.log(1)
  }
}
</script>