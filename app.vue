<template>
  <div id="app">
      <ais-instant-search :search-client="searchClient" index-name="articles">
          <NuxtLayout>
            <NuxtPage />
          </NuxtLayout>
      </ais-instant-search>
  </div>
</template>

<script>
import { AisInstantSearch } from 'vue-instantsearch/vue3/es';
import algoliasearch from 'algoliasearch/lite';

const searchClient = algoliasearch(
    '0WZQ1LXXOX',
    '6880056ab00e9c73c852a2d47cf0fc58'
);

export default {
    components: {
        AisInstantSearch,
    },
    data() {
        return {
            searchClient,
        };
    },
};
</script>

<style>
#app {
    font-family: 'Roboto', sans-serif;
}
</style>
