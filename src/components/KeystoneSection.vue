<template lang='pug'>
div
    v-parallax.parallax-size(:src='photos[state.currentPhotoIndex]' :class='{ "no-blur": !state.introductionVisible }')
        div.text-h3.mt-5.w-100.text-center.font-weight-bold.d-flex.align-center.flex-column.fill-height(:class='{ "justify-space-between": !state.introductionVisible }')
            div
                v-fade-transition
                    div.stroke(v-if='state.introductionVisible') Keystone Project
            v-fade-transition
                div.d-flex.align-center.justify-center.flex-column(v-if='state.introductionVisible' style='height: calc(100vh - 120px);')
                    div.stroke.text-h4.mb-2.font-weight-bold Washington, District of Columbia
                    div.stroke.text-h5.w-33.text-justify.font-weight-bold.mb-8
                        | A passion project in the making for the past 4 years, my keystone project persists in the form of this game.
                        | Boasting over 1.5 million individual game sessions, and having spawned a community of over 61,000 players, this project remains the crowning jewel of my portfolio.
                    v-btn.mx-2.text-capitalize(size='large' color='primary' @click='handleClickExplore') Explore
                //div.d-flex.align-center.fill-height.mb-5.flex-column.justify-end
            v-fade-transition
                div.mb-7.d-flex.justify-space-between.align-center.w-100(v-if='!state.introductionVisible')
                    v-btn.mx-2.text-capitalize(variant='plain' size='large' @click='handleClickPrevious' prepend-icon='mdi-arrow-left') Previous Image
                    div.d-flex.align-center.justify-center
                        v-btn.text-capitalize(variant='plain' size='large' href='https://www.roblox.com/games/3664995855/Washington-D-C') The Game
                        v-divider.mx-2.border-opacity-25(vertical color='white' :thickness='3')
                        v-btn(v-if='state.autoplay' icon variant='plain' tile size='large' @click='state.autoplay = false')
                            v-icon(size='x-large') mdi-pause
                        v-btn(v-else icon variant='plain' tile size='large' @click='state.autoplay = true')
                            v-icon(size='x-large') mdi-play
                        v-divider.mx-2.border-opacity-25(vertical color='white' :thickness='3')
                        v-btn.text-capitalize(variant='plain' size='large' @click='handleClickMoreInfo') More Info
                    v-btn.mx-2.text-capitalize(variant='plain' size='large' @click='handleClickNext' append-icon='mdi-arrow-right') Next Image
    v-dialog(v-model='state.moreInfoDialog.show' width='50%' )
        v-card
            v-card-title.mt-2.text-center About Washington, D.C.
            v-card-text.mt-0.text-justify
                | As the founder and primary developer of a thriving Roblox-based community, I have honed my skills in both game development and community management.
                | In addition to developing and maintaining our platform, I am responsible for overseeing day-to-day operations and interacting with our community of users,
                | advancing my people skills and furthering my understanding of the unique demands of digital community management.
            v-card-actions.d-flex.align-center.justify-center
                v-btn.text-capitalize.d-flex.align-center.justify-center(variant='text' @click='state.moreInfoDialog.show = false' prepend-icon='mdi-close-circle' ) Close
</template>

<script lang='ts'>
export default {
    name: "KeystoneSection"
}
</script>

<script setup lang='ts'>
import { onMounted, onUnmounted, reactive } from 'vue'

const state = reactive({
    introductionVisible: true,
    autoplay: true,
    currentPhotoIndex: 0,
    moreInfoDialog: {
        show: false
    },
    rotateInterval: null as ReturnType<typeof setInterval> | null
})

function rotateKeystonePhoto() {
    if (state.introductionVisible || !state.autoplay) return
    state.currentPhotoIndex = state.currentPhotoIndex === photos.length - 1 ? 0 : state.currentPhotoIndex + 1
}

onMounted(() => {
    state.rotateInterval = setInterval(rotateKeystonePhoto, 5000)
})

onUnmounted(() => {
    if (!state.rotateInterval) return
    clearInterval(state.rotateInterval)
})

const photos = [
    'https://media.discordapp.net/attachments/613219402334339092/1051655801695125584/image.png?width=1016&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1132069771408580679/image.png?width=1760&height=905',
    'https://media.discordapp.net/attachments/613219402334339092/1132069234348933230/image.png?width=1424&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1129923988202737714/image.png?width=1372&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1122632270038192128/image.png?width=1364&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1114320029102637168/image.png?width=1440&height=700',
    'https://media.discordapp.net/attachments/613219402334339092/1113227028938903653/image.png?width=1373&height=701',
    'https://media.discordapp.net/attachments/613219402334339092/1101917736881369118/image.png?width=1348&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1090119588139765830/image.png?width=1323&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1090115862574403594/image.png?width=1301&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1087943915669311498/image.png?width=1390&height=701',
    'https://media.discordapp.net/attachments/613219402334339092/1087538861921534014/image.png?width=1368&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1087055697306460190/RobloxScreenShot20230318_155152082.png?width=1335&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1086696229339136130/image.png?width=1381&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1083548213438586970/image.png?width=1426&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1072344027086737418/image.png?width=1418&height=702',
    'https://media.discordapp.net/attachments/613219402334339092/1058954492613230622/image.png?width=1440&height=692',
]

function handleClickExplore() {
    state.introductionVisible = false
}

function handleClickMoreInfo() {
    state.moreInfoDialog.show = true
}

function handleClickNext() {
    state.currentPhotoIndex = state.currentPhotoIndex === photos.length - 1 ? 0 : state.currentPhotoIndex + 1
    state.autoplay = false
}

function handleClickPrevious() {
    state.currentPhotoIndex = state.currentPhotoIndex === 0 ? photos.length - 1 : state.currentPhotoIndex - 1
    state.autoplay = false
}

defineExpose({
    handleClickExplore,
    handleClickMoreInfo,
    handleClickNext,
    handleClickPrevious
})
</script>

<style scoped>
.keystone-background-color {
    background-color: rgba(var(--v-theme-surface));
}

.parallax-width {
    width: 100%;
}

.stroke {
    -webkit-text-fill-color: white;
    -webkit-text-stroke-width: 0px;
    -webkit-text-stroke-color: black;
}
</style>

<style>
.no-blur img {
    filter: none !important;
}

.v-carousel-item img {
    filter: none !important;
}
</style>
