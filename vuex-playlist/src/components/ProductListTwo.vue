<template>
  <div id="product-list-two">
    <h2>Product List Two</h2>
      <ul>
          <li v-for="product in saleProducts" 
          :Key="product.name"
          >
          <span class="name">{{ product.name }}</span>
          <span class="price">${{ product.price }}</span>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  computed:{
    products(){
      return this.$store.state.products
    },    
    saleProducts(){
      return this.$store.getters.saleProducts;
    }
  }
}
</script>
<style scoped>
#product-list-two{
  background: lightseagreen;
  box-shadow: 1px 2px 3px rgba(red, green, blue, alpha);
  margin-bottom: 30px;
  padding: 10px 20px;
}
#product-list-two li{
  display: inline-block;
  margin-right:10px;
  margin-top: 10px;
  padding: 20px;
  background: lime;
}
#product-list-two li  .price{
  color: peru;
}
</style>
