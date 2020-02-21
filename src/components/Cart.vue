<template>
  <transition name="cart">
    <div class="cart-mask">
      <div class="cart-wrapper">
        <div class="cart-container">
          <div class="cart-header">
            <span>Carrinho de Compras</span>
          </div>
          <hr />
          <div class="cart-body">
            <div v-if="products !== null">
              <div :key="product.name" v-for="product in products">
                <div class="cart-item">
                  <img v-bind:src="product.images[0].imageUrl" alt class="cart-item_image" />
                  <div class="cart-item_desc">
                    <h3 class="cart-item_title">{{product.name}}</h3>
                    <p
                      class="cart-item_price"
                    >{{product.quantity}} x R${{Number(product.Value).toFixed()}},00</p>
                  </div>
                </div>
              </div>
            </div>
            <div v-if="products.isEmpty" class="cart-item">
              <span class="cart-item_title">carrinho de compras está vazio</span>
            </div>
            <div class="cart-total">
              <span>Total: R${{Number(total).toFixed()}},00</span>
            </div>
          </div>
          <hr />
          <div class="cart-footer">
            <div class="cart-actions">
              <button class="cart-btn cart-btn_outlined" @click="$emit('close')">
                <span class="cart-btn_text">fechar</span>
              </button>
              <button class="cart-btn" @click="$emit('close')">
                <span class="cart-btn_text">comprar</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Product",
  props: {
    products: Array
  },
  data() {
    return {
      total: 0
    };
  },
  created() {
    this.calcTotal();
  },
  methods: {
    calcTotal() {
      let result = 0;
      this.products.forEach(product => {
        result = result + product.total;
      });

      this.total = result;
    }
  }
};
</script>

<style lang="scss">
$btn-primary_color: hsl(122, 39, 49);
$btn-darker_color: hsl(122, 39, 30);
$btn-secondary_color: #fff;
.cart-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: row;
  transition: opacity 0.3s ease;
  justify-content: flex-end;
}

.cart-wrapper {
  display: table-cell;
  vertical-align: middle;
}
.cart-footer {
  margin: 1rem 0 2rem 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.cart-container {
  width: 300px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
  overflow: scroll;
  height: 100vh;
}

.cart-header h3 {
  margin-top: 0;
}

.cart-body {
  margin: 20px 0;
}

.cart-default-button {
  float: right;
}

.cart-enter {
  opacity: 0;
}

.cart-leave-active {
  opacity: 0;
}

.cart-enter .cart-container,
.cart-leave-active .cart-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
.cart-item {
  align-items: center;
  margin: 2rem 0 0 1rem;
  padding: 5px;
  width: 80%;
  height: 100px;
  display: flex;
  justify-content: center;
  flex-direction: row;
  border-radius: 7px;
  text-align: center;
  align-items: center;
}

.cart-item_title {
  text-align: left;
  font-size: 12px;
  font-weight: 700;
  margin: 20px 0;
}
.cart-item_price {
  margin: -1rem 0 0 1rem;
  font-weight: 400;
  font-size: 13px;
}
.cart-item_image {
  width: 100px;
}
.cart-btn_text {
  font-size: 14px;
  text-transform: capitalize;
}
.cart-btn {
  margin: 0 1rem;
  display: flex;
  flex-direction: row;
  background-color: $btn-primary_color;
  border: 1px solid $btn-primary_color;
  line-height: 2;
  padding: 0 20px;
  border-radius: 5px;
  color: $btn-secondary_color;
  cursor: pointer;
  &:hover {
    background-color: $btn-darker_color;
    font-weight: 600;
  }
}
.cart-btn_outlined {
  background-color: $btn-secondary_color;
  color: $btn-primary_color;
  border: 1px solid $btn-primary_color;
  &:hover {
    background-color: $btn-primary_color;
    color: $btn-secondary_color;
    font-weight: 600;
  }
}
.cart-item_desc {
  display: flex;
  flex-direction: column;
  margin: 10px;
}
.cart-actions {
  display: flex;
  flex-direction: row;
}
.cart-total {
  font-weight: 600;
  margin: 30px 10px;
}
</style>
