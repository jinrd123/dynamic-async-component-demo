<template>
    <h1>List</h1>
    <ul>
        <li
            v-for="n in 10"
            :key="n"
        >list item {{ n }}</li>
    </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    setup () {
        

        return {}
    }
})
</script>

<style scoped>

</style>