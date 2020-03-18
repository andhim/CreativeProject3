<template>
<div class="wrapper">
  <div class="cats">
  <p v-if="cart.length === 0">You didn't like any cats!</p>
    <div class="cat" v-for="cat in cart" :key="cat.id">
      <div class="info">
        <h1>{{cat.name}}</h1>
        <p>{{cat.category}}</p>
      </div>
      <div class="image">
        <img :src="'/images/'+cat.image">
      </div>
      <div class="gender">
        <h2>{{cat.gender}}</h2>
        <button class="auto" @click="remove(cat)">Remove</button>
      </div>
      <div class="quantity">
        <h3> Quantity: {{callQuantity(cat)}}</h3>
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
    remove(cat) {
        const removedCart = this.$root.$data.cart.filter(item => item !==cat);
        this.$root.$data.cart = removedCart;

    },
    callQuantity(cat) {
      const amount = this.$root.$data.quantity[cat.id - 1];
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

.cats {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.cat {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.cat img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.cat .image {
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
