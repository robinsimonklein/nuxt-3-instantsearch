<template>
    <div class="article-card">
        <NuxtLink class="article-card__image" :to="article.url" target="_blank" external>
            <img :src="article.urlToImage" :alt="article.title" />
        </NuxtLink>
        <div class="article-card__content">
            <NuxtLink class="article-card__link" :to="article.url" target="_blank" external>
                <h2 class="article-card__title">{{ article.title }}</h2>
            </NuxtLink>
            <p class="article-card__author">Author : {{ article.author }}</p>
        </div>
    </div>
</template>

<script setup>
defineProps({
    article: {
        type: Object,
        required: true
    }
})
</script>

<style lang="scss">
.article-card {
    &__image {
        display: block;
        aspect-ratio: 3/2;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

    &__link {
        color: black;
        text-decoration: none;

        &:hover {
            text-decoration: underline;
        }
    }

    &__author {
        color: #777;
    }
}
</style>
