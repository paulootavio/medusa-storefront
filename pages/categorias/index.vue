<script setup lang="ts">
// integre aqui com a api de categorias/colecoes
// api de categorias: https://docs.medusajs.com/api/store#product-categories_getproductcategories
// api de colecoes: https://docs.medusajs.com/api/store#product-collections_getcollections
const client = useMedusaClient();
debugger
const { product_categories } = await client.productCategories.list();
const filter = ref("");
</script>

<template>
  Categorias / Coleções


<div class="bg-gray-100">
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
    <div class="mx-auto max-w-2xl py-16 sm:py-24 lg:max-w-none lg:py-32">
      <h2 class="text-2xl font-bold text-gray-900">Categorias</h2>
      <div class="mt-6 space-y-12 lg:grid lg:grid-cols-3 lg:gap-x-6 lg:space-y-0">
        <div v-for="productCategorie in product_categories" :key="productCategorie.id" class="group relative">
          <div class="relative h-80 w-full overflow-hidden rounded-lg bg-white sm:aspect-h-1 sm:aspect-w-2 lg:aspect-h-1 lg:aspect-w-1 group-hover:opacity-75 sm:h-64">
         
            </div>
            <h3 class="mt-6 text-sm text-gray-500">
              <nuxt-link :to="`/categorias/${productCategorie.id}`">
                <span class="absolute inset-0" />
                {{ productCategorie.name }}
              </nuxt-link>
            </h3>
            <p class="text-base font-semibold text-gray-900">{{ productCategorie.description }}</p>
        </div>
      </div>
    </div>
  </div>
</div>

</template>

