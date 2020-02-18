<template>
  <div class="sku-body">
    <img v-bind:src="product.images[0].imageUrl" alt class="sku-image" />
    <h3 class="sku-title">{{product.name}}</h3>
    <p class="sku-price">R${{Number(product.Value).toFixed()}},00</p>
    <button class="btn" @click="addToCart">
      <em class="material-icons md-18 btn-ico">add</em>
      <span class="btn-text">Add to Cart</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    product: Object
  },
  methods: {
    addToCart({ product }) {
      this.$emit("add-to-cart", product);
    }
  }
};
</script>

<style lang="scss">
$btn-primary_color: hsl(122, 39, 49);
$btn-secondary_color: hsl(122, 39, 30);
$btn-text_color: #fff;
.sku-body {
  align-items: center;
  margin: 2rem 0 0 1rem;
  padding: 5px;
  width: 220px;
  height: 300px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  border-radius: 7px;
  text-align: center;
  align-items: center;
  &:hover {
    box-shadow: 0 0 11px rgba(33, 33, 33, 0.2);
  }
}

.sku-title {
  font-weight: 100;
  text-align: left;
  width: 200px;
  font-size: 14px;
  font-weight: 700;
}
.sku-price {
  margin: -1rem 0 0 1rem;
  font-weight: 400;
  font-size: 13px;
}
.sku-image {
  width: 200px;
}
.btn {
  display: flex;
  flex-direction: row;
  background-color: $btn-primary_color;
  border: 0;
  line-height: 2;
  padding: 0 20px;
  border-radius: 5px;
  margin: 2px;
  cursor: pointer;
  &:hover {
    background-color: $btn-secondary_color;
    // box-shadow: 0px 0px 6px 0px rgba(0, 0, 0, 0.75);
  }
}
.btn-text {
  color: $btn-text_color;
  font-size: 1rem;
}
.btn-ico {
  color: $btn-text_color;
  align-items: center;
  justify-content: center;
  margin: 4px 2px 0 0;
}
</style>
