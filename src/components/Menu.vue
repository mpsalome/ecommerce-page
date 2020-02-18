<template>
  <div class="menu-body">
    <span class="menu-text menu-item menu-title">Minha Loja</span>
    <hr class="menu-item menu-line" />
    <span class="menu-text menu-item">Perfumaria</span>
    <span class="menu-text menu-item">Maquiagem</span>
    <span class="menu-text menu-item">Cabelos</span>
    <span class="menu-text menu-item">Infantil</span>
    <div class="image-box">
      <em class="material-icons md-18 menu-ico">shopping_cart</em>
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

$dark-color: #737171;

$menu-font_family: "Robot", sans-serif;
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
  border-bottom: 1px solid $line-color;
  font-family: $menu-font_family;
}
.menu-item {
  margin: 0 1rem 0 2rem;
}
.menu-title {
  font-weight: 700;
  color: $dark-color;
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
.menu-ico {
  color: $dark-color;
}
* :hover {
  cursor: pointer;
}
</style>
