<template>
 <div class="container-fluid">
  <nav class="navbar navbar-light bg-light">
    <a class="navbar-brand">Dashboard</a>
    <button class="btn btn-danger btn-sm" @click="logout">Logout</button>
  </nav>
  <br>
  <router-link to="/addProduct"><button type="button" class="btn btn-info btn-sm">Add Product</button></router-link>
  <br>
  <div class="container">
    <div class="row title">
      <h2>Products</h2>
    </div>
    <br>
    <div class="row">
      <ProductCard
        v-for='product in products'
        :key='product.id'
        :product='product'
      />
    </div>
  </div>
 </div>
</template>

<script>

import ProductCard from '../components/ProductCard'

export default {
  name: 'Products',
  components: {
    ProductCard
  },
  methods: {
    logout () {
      localStorage.clear()
      this.$router.push('/login')
    }
  },
  computed: {
    products () {
      return this.$store.state.products
    }
  },
  created () {
    this.$store.dispatch('fetchProducts')
  }
}
</script>

<style lang="css" scoped>
.container-fluid {
  justify-content: center;
  justify-items: center;
  align-items: center;
  display: flexbox;
  padding: 0px;
  margin : 0px
}

.btn {
  padding: 7px;
  margin: 5px;
}
.card-body {
  flex: 1 1 auto;
  min-height: 1px;
  padding: 5px;
}
</style>
