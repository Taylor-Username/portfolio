<template lang='pug'>
v-app
    v-main
        //NavBar
        div.d-flex.align-center.justify-center
            router-view
</template>

<script lang="ts" setup>
import NavBar from '@/components/NavBar.vue'
</script>
