<template>
<div class="wrapper">
  <h1>{{this.$root.$data.emptyMessage}}</h1>
  <div class="products">
    <div class="product" v-for="product in this.$root.$data.cart" :key="product.id">
      <div class="info">
        <h1>{{product.name}}</h1>
        <p>{{product.country}}</p>
      </div>
      <div class="image">
        <img :src="'/images/products/'+product.image">
      </div>
      <div class="price">
        <h2>{{product.price}}</h2>
        <button v-on:click="removeFromCart(product.id)" class="auto"> Remove </button>
      </div>
    </div>
  </div>
</div>
</template>


<script>

export default {
  name: 'Items',
  props: {
    products: Array
  },
  data() {
    return {
      cart: [],

    }
  },
  methods: {
    removeFromCart(productToRemove) {
      if ( this.$root.$data.cart.length === 1) {
      this.$root.$data.emptyMessage = "Your cart is empty!"
      }
      for (var i = 0; i < this.$root.$data.cart.length; i += 1) {
        if (productToRemove === this.$root.$data.cart[i].id) {
          this.$root.$data.cart.splice(i, 1);
          break;
        }
      }
    },

  }
}

</script>




<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.product img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
  border-radius: 3px;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #F2921D;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
  border-radius: 5px;
}

.auto {
  margin-left: auto;
}
</style>
