<template>
  <div class="menu-body">
    <span class="menu-text menu-item menu-title">Minha Loja</span>
    <hr class="menu-item menu-line" />
    <span class="menu-text menu-item">Perfumaria</span>
    <span class="menu-text menu-item">Maquiagem</span>
    <span class="menu-text menu-item">Cabelos</span>
    <span class="menu-text menu-item">Infantil</span>
    <div class="image-box">
      <i class="material-icons md-18" style="color:#737171">shopping_cart</i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Menu"
};
</script>

<style lang="scss" scoped>
$gradient-color_start: #fefefe;
$gradient-color_end: #fbfbfb;
$font-color: #9c9a9a;
$line-color: #e2e2e2;
$title-color: #737171;
.menu-body {
  background-image: linear-gradient($gradient-color_start, $gradient-color_end);
  top: 0;
  width: 100%;
  font-family: sans-serif;
  height: 90px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;
  font-family: "Roboto", sans-serif;
  border-bottom: 1px solid $line-color;
}
.menu-item {
  margin: 0 1rem 0 2rem;
}
.menu-title {
  font-weight: 700;
  color: $title-color !important;
}
.menu-text {
  text-transform: uppercase;
  color: $font-color;
}
.menu-line {
  border: none;
  border-left: 1px solid $line-color;
  height: 20px;
  width: 1px;
  cursor: default !important;
}
.image-box {
  display: flex;
  border: 1px solid $line-color;
  border-radius: 20px;
  align-items: center;
  margin-left: auto;
  margin-right: 1rem;
  width: auto;
  padding: 6px;
  width: 2rem;
  justify-content: center;
}
* :hover {
  cursor: pointer;
}
</style>
