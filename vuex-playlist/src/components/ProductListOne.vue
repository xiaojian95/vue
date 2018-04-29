<template>
  <div id="product-list-one">
      <h2>Product List One</h2>
      <ul>
          <li v-for="product in saleProducts" 
          :Key="product.name"
          >
          <span class="name">{{ product.name }}</span>
          <span class="price">${{ product.price }}</span>
          </li>
      </ul>
      <button @click="reducePrice(4)">商品降价</button>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import{mapActions} from 'vuex'
export default {
  computed:{
    products(){
      return this.$store.state.products
    },
    /*...mapGetters([
      "saleProducts",
    ]),*/
    saleProducts(){
      var saleProducts=this.$store.state.products.map(
        product=>{
          return {
            name:"**"+product.name+"**",
            price:product.price/2,
          }
        });
        return saleProducts;
    }
  },
  methods:{
      ...mapActions([
        "reducePrice"
      ]),
      // reducePrice:function(amount){
      //   /*this.$store.state.products.forEach(product=>{
      //     product.price-=1;
      //   });*/
      //   //this.$store.commit('reducePrice');
      //   this.$store.dispatch('reducePrice',amount)
      // }
    }
}
</script>

<style scoped>
#product-list-one{
  background: #7A67EE;
  box-shadow: 1px 2px 3px rgba(red, green, blue, alpha);
  margin-bottom: 30px;
  padding: 10px 20px;
}
#product-list-one li{
  display: inline-block;
  margin-right:10px;
  margin-top: 10px;
  padding: 20px;
  background: lime;
}
#product-list-one li  .price{
  color: peru;
}
</style>
