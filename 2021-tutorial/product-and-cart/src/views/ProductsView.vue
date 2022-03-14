<template>
  <main class="wrapper">
    <h1>Products</h1>

    <div class="card-container">
      <ProductCard
        v-for="(product, i) in inventory"
        class="card"
        :key="product.id"
        :index="i"
        :product="product"
        :addToCart="addToCart"
      />
    </div>
  </main>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'

export default {
  name: 'HomeView',
  components: {
    ProductCard
  },
  props: ['inventory', 'addToCart']
}
</script>
