<script lang="ts" setup>
import useWpApi from "~~/composables/useWpApi";



const {data: posts} =await useWpApi().getPosts<any>();


</script>
<template>
   <main>
    <PageHeader>
                    <!--Image-->
            <div class="w-[200px] relative h-[200px] mr-7 rounded overflow-hidden shadow-md">
            <img src="~/assets/blog.jpg" 
                class="w-full h-full absolute object-cover"/>
             </div>



            <!--Header text-->
           <div>
            <h1 class="text-4xl font-bold mb-2">Sonal's Blog</h1>

            <p class="mb-4">
                I am final year Student at BBDNIIT and Google Developer Student Club Lead.<br>
                Writing blogs on latest technology.  
            </p>
            <a class="text-white bg-gradient-to-r from-purple-500 via-purple-600 to-purple-700 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-purple-300 dark:focus:ring-purple-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2" href="https://www.linkedin.com/in/sonal-maurya172602/">Let's Connect</a>
           </div> 

    </PageHeader>
     <!--Blog Grid Starts-->
    <section class="container py-16">
      <div class="grid sm:grid-cols-3 gap-10">
        <BlogCard
          v-for="post in posts"
          :key="post.id"
          :title="post.title.rendered"
          :excerpt="post.excerpt.rendered"
          :image="post._embedded['wp:featuredmedia'][0]?.source_url"
          :slug="post.slug"
        
        />
    
      </div>
    </section>
     <!--Blog Grid Ends-->
   </main>
</template>

