
<script lang="ts" setup>
import colorGenerator from "~~/utils/colorGenerator";


useHead({
  title: "Categories",
  meta: [
    {
      name: "description",
      content: "Categories",
    },
  ],
});


const{data: categories} = await useWpApi().getCategories<any>();
</script>
<template>
    <PageHeader title="Category Index"/>
    <section class="py-10 container">
        <div class="flex flex-wrap gap-5">
            <NuxtLink v-for="category in categories"
             :key="category.id" 
             :to="`/categories/${category.slug}`" 
             class="block py-2 px-4 bg-gray-300 rounded hover:bg-gray-400"
             :style="{ backgroundColor: colorGenerator() }"
             >
             
             <span class ="font-semibold">#{{ category.name }}</span>
            </NuxtLink>

        </div>


    </section>

      

</template>