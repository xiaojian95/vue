<script>
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export const store=new Vuex.Store({
    //strict:true,//严格模式
    state:{
        products:[
        {name:"马云",price:200},
        {name:"马化腾",price:150},
        {name:"马荣",price:100},
        {name:"马蓉",price:50}
        ]
    },
    getters:{
        saleProducts:(state)=>{
        var saleProducts=state.products.map(product=>{
                return {
                    name:"**"+product.name+"**",
                    price:product.price/4,
                }
            });
            return saleProducts;
        }
    },mutations:{
        reducePrice:(state,payload)=>{
            //setTimeout(()=>{
                state.products.forEach(product=>{
                product.price-=payload;
            });
            //},3000);
        }
    },actions:{
        reducePrice:(context,payload)=>{
            setTimeout(()=>{
                context.commit('reducePrice',payload);
            },2000);
        }
    }
})
</script>