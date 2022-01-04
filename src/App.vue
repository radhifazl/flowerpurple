<template>
  <cover-page />
  <new-header/>
  <roundown-acara />
</template>

<script>
import CoverPage from './components/CoverPage.vue'
import NewHeader from './components/NewHeader.vue'
import RoundownAcara from './components/RoundownAcara.vue'

export default {
  name: 'App',
  components: {
    NewHeader,
    RoundownAcara,
    CoverPage
  }
}
</script>

<style>
</style>
