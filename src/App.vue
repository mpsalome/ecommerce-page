<template>
  <div id="app">
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons" />
    <Menu v-on:click-cart="openCloseCart" />
    <div v-if="isCartOpen">
      <Cart :products="cart" v-on:close="openCloseCart" />
    </div>
    <div class="call-to-action">
      <hr class="line" />
      <span class="title">últimos produtos</span>
      <hr class="line" />
    </div>
    <div class="product-container">
      <div :key="product.name" v-for="product in productList">
        <Product :product="product" v-on:add-to-cart="(addToCart(product))" />
      </div>
    </div>
  </div>
</template>

<script>
import Menu from "@/components/Menu";
import Product from "@/components/Product";
import productList from "@/assets/products.json";
import Cart from "@/components/Cart";
export default {
  name: "app",
  components: {
    Menu,
    Product,
    Cart
  },
  data() {
    return {
      productList,
      cart: [],
      isCartOpen: false
    };
  },
  methods: {
    openCloseCart() {
      this.isCartOpen = !this.isCartOpen;
    },
    addToCart(product) {
      let indexInCart = this.search(product.name, this.cart);
      if (indexInCart != null) {
        let existingItem = this.cart[indexInCart];
        existingItem.quantity++;
        existingItem.total = product.Value * existingItem.quantity;
        this.cart[indexInCart] = existingItem;
      } else {
        let qtt = 1;
        let total = product.Value * qtt;
        let cartItem = {
          name: product.name,
          total: total,
          quantity: qtt,
          images: product.images,
          Value: product.Value
        };
        this.cart.push(cartItem);
      }
      // eslint-disable-next-line
      console.table(this.cart);
    },
    search(nameKey, array) {
      for (var i = 0; i < array.length; i++) {
        if (array[i].name === nameKey) {
          return i;
        }
      }
    }
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap");
$line-color: #fbfbfb;
$title-color: #817e7e;
$body-font_family: "Roboto", sans-serif;
body {
  margin: 0 0 60px 0 !important;
  padding: 0;
  font-family: $body-font_family;
}
.product-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0 0.5rem;
  padding: 2rem;
}
.call-to-action {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin: 2rem 0 0 0;
}
.title {
  text-transform: uppercase;
  letter-spacing: 1px;
  color: $title-color;
}
.line {
  border-left: 1px solid $line-color;
  display: inline;
  margin: 0 2rem;
  width: 100px;
  height: 0;
  border-style: inset;
}
</style>
