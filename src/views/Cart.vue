<template>
<div class="wrapper">
    <div v-if="numItems() > 0">
        <div class="cart">
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
                    <button class="auto" @click="RemoveFromCart(product)">Remove From Cart</button>
                </div>
            </div>
        </div>
    </div>
    <div v-else>
        <p>Cart is empty.</p>
    </div>
</div>
</template>


<script>
export default {
  name: 'Cart',
  computed: {
      cart() {
          return this.$root.$data.cart;
      }
  },
  methods: {
    RemoveFromCart(item) {
        var value = this.$root.$data.cart.indexOf(item);
        this.$root.$data.cart.splice(value, 1);
    },
    numItems() {
      return this.$root.$data.cart.length
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

.cart {
    background-color: grey;
    border: 4px solid black;
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
}

.auto {
  margin-left: auto;
}

</style>