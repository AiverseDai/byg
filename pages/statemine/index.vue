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

  middleware({ store }) {
    // If the user is not authenticated
    const prefix = store.getters.currentUrlPrefix
    if (prefix !== 'statemine') {
      this.$consola.log('Not statemine')
      store.dispatch('setUrlPrefix', 'statemine')
    }
  }
}
</script>
