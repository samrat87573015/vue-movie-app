
<template>
  <main>
    <div class="container mx-auto py-8">
      

      <div class="grid grid-cols-12 gap-6 pt-6">
        <div v-for="product in products" class="lg:col-span-4 sm:col-span-6 col-span-12 shadow">
          <div class="product_itam">
            <div class="relative">
              <img class="w-full h-[300px] object-cover" :src="product.thumbnail" alt="">
              <span class="absolute bottom-3 left-3 capitalize text-white bg-green-500 inline-block py-1 px-3 rounded-sm">{{ product.category }}</span>
            </div>
            <div class="movie_content p-6">
              <p>Brand: {{ product.brand }}</p>
              <h2 class="text-xl font-bold text-gray-800 mb-3">{{ product.title }}</h2>
              
              <p class="text-gray-500">{{ product.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>


<script>

import axios from 'axios'

export default {

  name: 'Home',

  data(){
    return{
      products: []
    }
  },
  
  mounted(){
    axios.get('https://dummyjson.com/products')
    .then(response => {
      this.products = response.data.products

    })
  }
}
</script>