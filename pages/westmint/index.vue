<template>
  <Landing prefix="statemine" buildOn="Statemine Unique Pallet" />
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {
    Landing: () => import('@/components/landing/Landing.vue'),
  },
})
export default class LandingPage extends Vue {
  layout() {
    return 'full-width-layout'
  }

  middleware({ store, route }) {
    const prefix = store.getters.currentUrlPrefix
    if (prefix !== route.name) {
      this.$consola.log('[EXPECT]', route.name, 'got', prefix)
      store.dispatch('setUrlPrefix', route.name)
    }
  }
}
</script>
