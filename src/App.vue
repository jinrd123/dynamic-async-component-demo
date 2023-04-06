<template>
  <ComponentTab />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ComponentTab from './components/ComponentTab.vue';

export default defineComponent({
  name: "App",
  components: {
    ComponentTab
  }
})

</script>

<style scoped>

</style>
