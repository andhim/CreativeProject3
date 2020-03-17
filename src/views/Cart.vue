<template>
<div class="wrapper">
  <div class="products">
  <p v-if="cart.length === 0">Your shopping cart is empty</p>
    <div class="product" v-for="product in cart" :key="product.id">
      <div class="info">
        <h1>{{product.name}}</h1>
        <p>{{product.country}}</p>
      </div>
      <div class="image">
        <img :src="'/images/products/'+product.image">
      </div>
      <div class="price">
        <h2>{{product.price}}</h2>
        <button class="auto" @click="remove(product)">Remove</button>
      </div>
      <div class="quantity">
        <h3> Quantity: {{callQuantity(product)}}</h3>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Cart',
  
  computed: {
    cart() {
      return this.$root.$data.cart;
    },
  },
  methods : {
    remove(product) {
      //if (this.$root.$data.quantity[product.id - 1] === 0) {
        const removedCart = this.$root.$data.cart.filter(item => item !==product); 
        this.$root.$data.cart = removedCart;

    },
    callQuantity(product) {
      const amount = this.$root.$data.quantity[product.id - 1];
      return amount;
    }
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
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #FF0000;
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

.quantity {
  display: flex;
  justify-content: center;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}


</style>