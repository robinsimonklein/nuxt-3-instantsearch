<template>
    <div class="layout">
        <div class="container">
            <header>
                <h1>Nuxt 3 + InstantSearch with SSR ⚡️</h1>
                <AisSearchBox class="search" />
            </header>
            <slot />
        </div>
    </div>
</template>

<script setup>
import {AisSearchBox} from 'vue-instantsearch/vue3/es';
</script>

<style lang="scss">
.container {
    max-width: 1100px;
    margin-left: auto;
    margin-right: auto;
    padding-left: 30px;
    padding-right: 30px;
}

.search {

    form {
        display: flex;
        align-items: center;
        width: 100%;
    }

    input {
        flex: 1;
        padding: 1rem;
        font-size: 20px;
    }

    button {
        width: 30px;
        height: 30px;
        margin-left: 15px;
    }
}
</style>
