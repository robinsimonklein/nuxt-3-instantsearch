<template>
  <div id="app">
      <AisInstantSearchSsr>
          <NuxtLayout>
            <NuxtPage />
          </NuxtLayout>
      </AisInstantSearchSsr>
  </div>
</template>

<script>
import {AisInstantSearchSsr, createServerRootMixin} from 'vue-instantsearch/vue3/es';
import algoliasearch from 'algoliasearch/lite';
import { renderToString } from '@vue/server-renderer';

function _renderToString(app) {
    return new Promise((resolve, reject) => {
        renderToString(app, (err, res) => {
            if (err) reject(err);
            resolve(res);
        });
    });
}

const searchClient = algoliasearch(
    '0WZQ1LXXOX',
    '6880056ab00e9c73c852a2d47cf0fc58'
);

export default {
    mixins: [
        createServerRootMixin({
            searchClient,
            indexName: 'articles',
        }),
    ],
    serverPrefetch() {
        return this.instantsearch
            .findResultsState({
                component: this,
                renderToString: _renderToString,
            }).then(algoliaState => {
                this.$ssrContext.nuxt.algoliaState = algoliaState;
            });
    },
    beforeMount() {
        const results =
            (this.$nuxt.context && this.$nuxt.context.nuxtState.algoliaState) ||
            window.__NUXT__.algoliaState;

        this.instantsearch.hydrate(results);

        // Remove the SSR state so it can't be applied again by mistake
        delete this.$nuxt.context.nuxtState.algoliaState;
        delete window.__NUXT__.algoliaState;
    },
    components: {
        AisInstantSearchSsr,
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
