<template lang='pug'>
div.snap-container
    MenuSection.scroll-snap.menu-section
    div.d-flex.align-center.justify-center.flex-column.divider-background-color.elevation-10(style='height:2vh;')
    KeystoneSection.scroll-snap(ref='keystone')
    AboutSection.scroll-snap(ref='about')
    WorkSection.scroll-snap(ref='work')
    ContactSection.scroll-snap(ref='contact')
</template>

<script lang="ts" setup>
import KeystoneSection from '@/components/KeystoneSection.vue'
import AboutSection from '@/components/AboutSection.vue'
import MenuSection from '@/components/MenuSection.vue'
import WorkSection from '@/components/WorkSection.vue'
import ContactSection from '@/components/ContactSection.vue'

import { provide, ref } from 'vue'

const about = ref(null)
const work = ref(null)
const keystone = ref(null)
const contact = ref(null)

function scrollToAbout() {
    if (!about.value) return
    (about.value['$el'] as HTMLElement).scrollIntoView({ behavior: 'smooth' })
}

function scrollToWork() {
    if (!work.value) return
    (work.value['$el'] as HTMLElement).scrollIntoView({ behavior: 'smooth' })
}

function scrollToKeystone() {
    if (!keystone.value) return
    (keystone.value['$el'] as HTMLElement).scrollIntoView({ behavior: 'smooth' })
}

function scrollToContact() {
    if (!contact.value) return
    (contact.value['$el'] as HTMLElement).scrollIntoView({ behavior: 'smooth' })
}

provide('scrollTo', {
    about: scrollToAbout,
    work: scrollToWork,
    keystone: scrollToKeystone,
    contact: scrollToContact
})
</script>

<style>
.divider-background-color {
    background-color: rgba(var(--v-theme-surface));
}

.scroll-snap {
    scroll-snap-align: start;
}

.parallax-size {
    width: 100vw;
    height: 100vh;
}

.v-img__img--cover {
    filter: blur(6px);
}

div, h1, span {
    text-shadow: 1px 2px 2px black;
}
</style>
