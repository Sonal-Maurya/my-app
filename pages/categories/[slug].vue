<script lang="ts" setup>
const route  = useRoute();

//get Category ID
const {data: categories} = await useWpApi().get<any>(`categories?slug=${route.params.slug}`);

// get Post Related
const {data: posts} = await useWpApi().getPosts<any>(categories.value[0].id);
  
</script>
<template>
    <PageHeader :title="`Archive: ${categories[0].name}`"/>
    <section class="container py-12">
        <div class="grid sm:grid-cols-3 gap-5">
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
</template>
<style>
.post-content h1,
.post-content h2,
.post-content h3,
.post-content h4,
.post-content h5,
.post-content h6 {
   @apply mb-3 font-bold;
}
.post-content p{
    @apply mb-2;
}
.post-content img{
    @apply my-4;
}

.post-content h1{
    @apply text-3xl;
}

.post-content h2{
    @apply text-2xl;
}

.post-content h3{
    @apply text-xl;
}

.post-content h4{
    @apply text-lg;
}

.post-content h1{
    @apply text-base;
}

.post-content h1{
    @apply text-sm;
}



</style>
 