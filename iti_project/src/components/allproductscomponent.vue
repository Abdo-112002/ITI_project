<template>
                <div class="d-flex flex-row flex-wrap justify-content-around">
                    <div  v-for="product in allproducts" :key="product.price" class="card my-3 py-3" style="width:20rem;">
                        <img :src="product.image" class="card-img-top product-img" style="">
                        <div class="card-body" >
                            <h5 class="card-title text-center"><a class="text-dark" href="#">{{product.name}}</a> </h5>
                            <h6 class="card-text my-3">{{product.price}} $</h6>
                            <div class="text-center">
                                <button class="btn btn-success px-5" @click="addProductToCart(product)">Add to cart <i class="fa-solid fa-cart-shopping"></i></button>
                            </div>
                        </div>
                    </div>
                </div>
 
</template>
<script>
//  import students from '../students'

import allproductscomponent from './allproductscomponent.vue'


export default {
    async created(){
      const res= await fetch("http://localhost:3000/allproducts");
      this.allproducts=await res.json();
    },
    props : ['addProductToCart'],
    data(){
        return{
        allproducts : [],
        }
    },components:{
    allproductscomponent,
    },
}


</script>