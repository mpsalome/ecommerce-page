<template>
  <div class="sku-body">
    <img v-bind:src="image.imageUrl" alt class="sku-image" />
    <h3 class="sku-title">{{name}}</h3>
    <p class="sku-price">R${{Number(value).toFixed()}},00</p>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    name: String,
    value: Number,
    image: Object
  }
};
</script>

<style lang="scss">
$secondary-color: #fff;
.sku-body {
  align-items: center;
  margin: 2rem 0 0 1rem;
  font-family: "Roboto", sans-serif;
}
.sku-title {
  font-weight: 100;
  text-align: left;
  width: 200px;
  font-size: 14px;
}
.sku-price {
  margin: -1rem 0 0 1rem;
  font-size: 12px;
}
.sku-image {
  width: 200px;
}
</style>
