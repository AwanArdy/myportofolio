<template>
    <div class="max-w-4xl mx-auto px-4 py-8">
        <h1 class="text-3xl font-bold mb-6">Blog</h1>

        <div class="flex flex-wrap gap-6">
            <NuxtLink
                v-for="post in posts"
                :key="post._path"
                :to="post._path"
                class="w-full md:w-[48%] bg-white dark:bg-zinc-900 shadow rounded-xl p-4 hover:border-l-4 border-blue-500 transition-all"
            >
                <h2 class="text-xl font-semibold">{{ post.title }}</h2>
                <p class="text-sm text-gray-500">{{ post.date }}</p>
                <p class="mt-2 text-gray-700 dark:text-gray-300">
                    {{ post.description }}
                </p>
            </NuxtLink>
        </div>
    </div>
</template>

<script setup lang="ts">
const { data: posts } = await useAsyncData("blog-posts", () =>
    queryContent("/blog").sort({ date: -1 }).find(),
);
</script>
