<script setup lang="ts">
const client = useMedusaClient();
const route=useRoute()
const  { products }  = await client.products.list({limit: 10,category_id: [route.params.id.toString()]});
const mobileFiltersOpen = ref(false)
</script>

<template>


<section class="container my-40">
  <div class="grid grid-cols-[repeat(auto-fill,_minmax(280px,_1fr))] gap-4">
    <ProductCard v-for="product in products" 
      :key="product.id" 
      :image="product.images ? product.images[0].url : ''" 
      :title="(product.title as string)" 
      :price="product.variants[0].prices[0].amount / 100"
      :handle="(product.handle as string)"
      :variant-id="(product.variants[0].id as string)"
    />
  </div>
</section>  
</template>