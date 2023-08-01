<template lang='pug'>
div.d-flex.align-center.justify-center.w-100.pa-10.about-background-color.align-center
    div.text-h5 Contact
    v-divider.mx-3.border-opacity-100(vertical :thickness='3' color='white')
    div.d-flex.text-h6
        v-icon.mr-2 mdi-email
        div #[a(href='mailto:TaylorJamesGlynn@gmail.com') TaylorJamesGlynn@gmail.com]
</template>

<script lang='ts'>
export default {
    name: "ContactSection"
}
</script>

<script setup lang='ts'>

</script>

<style scoped>
.about-background-color {
    background-color: rgba(var(--v-theme-surface));
}
</style>
