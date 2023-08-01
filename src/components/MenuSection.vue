<template lang='pug'>
v-parallax.parallax-size(src='https://images.unsplash.com/photo-1689784730988-6cafd0821f8b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2128&q=80')
    div.d-flex.fill-height.justify-center.align-center.text-white.flex-column
        h1.mb-8.text-h1.font-weight-bold Taylor Glynn
        div.d-flex
            v-btn.mx-2.text-capitalize.text-h5(variant='text' size='x-large' @click='handleClickScrollToKeystone') Keystone
            v-btn.mx-2.text-capitalize.text-h5(variant='text' size='x-large' @click='handleClickScrollToAbout') About
            v-btn.mx-2.text-capitalize.text-h5(variant='text' size='x-large' @click='handleClickScrollToWork') Projects
            v-btn.mx-2.text-capitalize.text-h5(variant='text' size='x-large' @click='handleClickScrollToContact') Contact
</template>

<script lang='ts'>
export default {
    name: "MenuSection"
}
</script>

<script setup lang='ts'>
import { inject } from 'vue'

interface ScrollTos {
    about: () => null
    work: () => null
    keystone: () => null
    contact: () => null
}

const scrollTos: ScrollTos | undefined = inject('scrollTo')

function handleClickScrollToAbout() {
    if (!scrollTos) return
    scrollTos.about()
}

function handleClickScrollToWork() {
    if (!scrollTos) return
    scrollTos.work()
}

function handleClickScrollToKeystone() {
    if (!scrollTos) return
    scrollTos.keystone()
}

function handleClickScrollToContact() {
    if (!scrollTos) return
    scrollTos.contact()
}

defineExpose({
    handleClickScrollToKeystone,
    handleClickScrollToAbout,
    handleClickScrollToWork,
    handleClickScrollToContact
})
</script>
