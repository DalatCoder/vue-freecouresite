<template>
  <div class="splash-container">
    <div class="splash">
      <h1>Splendid Food</h1>
    </div>
  </div>

  <main class="wrapper">
    <h2>Recommended</h2>

    <div class="recommended">
      <div
        v-for="(product, index) in inventory.slice(0, 3)"
        class="card"
        :key="product.id"
      >
        <div class="card-title">{{ product.name }}</div>
        <div class="card-body">
          <i class="icofont-10x icofont-{{ product.icon }}"></i>
          <form>
            <div class="row">
              <div class="cell">
                <label>Type:</label>
              </div>
              <div class="cell">
                <em>{{ product.type }}</em>
              </div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Price:</label>
              </div>
              <div class="cell">${{ product.price.USD }}</div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Quantity:</label>
              </div>
              <div class="cell">
                <input type="number" v-model.number="product.quantity" />
              </div>
            </div>
          </form>
        </div>
        <div class="card-footer">
          <button class="btn btn-light" @click="addToCart(product.name, index)">
            Add to cart
          </button>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  components: {},
  props: ['inventory', 'addToCart']
}
</script>
