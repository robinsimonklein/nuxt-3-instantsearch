<template>
    <div class="page">
        <div class="stats">

        </div>
        <AisHits class="articles">
            <template v-slot="{ items }">
                <div class="articles__grid">
                    <ArticleCard v-for="article in items" :key="article" :article="article" class="articles__item" />
                </div>
            </template>
        </AisHits>
        <AisPagination class="pagination" />
    </div>
</template>

<script setup>
import {AisHits, AisPagination} from "vue-instantsearch/vue3/es";
</script>

<style lang="scss">

.articles {
    margin-top: 30px;

    &__grid {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-column-gap: 20px;
        grid-row-gap: 25px;

        @media screen and (max-width: 900px) {
            grid-template-columns: 1fr 1fr;
        }

        @media screen and (max-width: 600px) {
            grid-template-columns: 1fr;
        }
    }
}

.pagination {
    margin: 40px 0;

    ul {
        display: flex;
        gap: 10px;
        align-items: center;
        justify-content: center;
        padding: 0;
        list-style: none;
    }
    .ais-Pagination-item {
        display: inline-block;
        width: 50px;
        background: #eee;
        text-align: center;

        &--selected {
            background: black;

            .ais-Pagination-link{
                color: white;
            }
        }
    }

    .ais-Pagination-link {
        display: inline-block;
        padding: 10px;
        text-decoration: none;
        color: #777777;
    }
}
</style>
