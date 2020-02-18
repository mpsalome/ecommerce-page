<template>
  <div id="app">
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons" />
    <Menu />
    <div class="call-to-action">
      <hr class="line" />
      <span class="title">últimos produtos</span>
      <hr class="line" />
    </div>
    <div class="product-container">
      <div :key="product.name" v-for="product in productList">
        <Product :product="product" />
      </div>
    </div>
  </div>
</template>

<script>
import Menu from "@/components/Menu";
import Product from "@/components/Product";
import productList from "@/assets/products.json";
export default {
  name: "app",
  components: {
    Menu,
    Product
  },
  data() {
    return {
      productList
    };
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
