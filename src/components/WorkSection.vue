<template lang='pug'>
div.background
    div.pa-10.text-h3.text-center.text-shadow Other Work
    div.pb-8.d-flex.align-center.justify-center.fill-height.flex-column
        v-row.my-4(v-for='(item, index) in workItems' no-gutters align='center' justify='center')
            v-col(style='width:50vw' cols='4' :order='index % 2 == 0 ? 2 : -2')
                v-fade-transition
                    v-img.elevation-6.rounded-lg(:src='item.image' width='50vw')
            v-col(cols='1' :order='index % 2 == 0 ? 1 : -1')
            v-col(style='width:50vw;' cols='4')
                div.px-6.d-flex.align-center.justify-center.flex-column
                    div.text-center.text-h6.font-weight-bold.text-shadow {{ item.title }}
                    div.text-shadow.text-justify {{ item.description }}
</template>

<script lang='ts'>
export default {
    name: "WorkSection"
}
</script>

<script setup lang='ts'>
import { reactive } from 'vue'

interface WorkItem {
    image: string
    title: string
    description: string
}

const state = reactive({
    workItemIndex: 0
})

const workItems: WorkItem[] = [
    {
        image: 'https://static.wixstatic.com/media/db664b_1d6fd6443b074a82bc569028edf79eb2~mv2.png/v1/crop/x_0,y_0,w_1278,h_641/fill/w_600,h_301,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/2.png',
        title: 'Rendering: Unity',
        description: 'Undertaking the creation of a render for a Star Wars base in Unity has been a rewarding endeavor that combines technical expertise with a passion for the beloved franchise. With keen attention to detail and a deep appreciation for the Star Wars universe, this project aims to provide fans with an immersive and visually captivating experience that brings iconic elements from the franchise to life.'
    },
    {
        image: 'https://static.wixstatic.com/media/db664b_fad85cfa3a9145b4bced8cfe950adba5~mv2.png/v1/fill/w_600,h_338,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/1.png',
        title: 'Game Level: Village Scene',
        description: 'A meticulously designed scene featuring characters engaging in lively interactions within a charming village, all crafted to replicate classic pixel-art texturing. This project showcases a harmonious fusion of creative ingenuity and technical expertise, providing viewers with an enchanting and nostalgia-inducing experience.'
    },
    {
        image: 'https://static.wixstatic.com/media/db664b_1a7fa22b3e6d41f1b6b5d4aa1f03f978~mv2.png/v1/fill/w_615,h_346,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/pic.png',
        title: 'Game Level: Post Office Lobby',
        description: 'Within the immersive world of this game, players will encounter a thoughtfully designed postal office lobby, meticulously crafted to evoke a sense of familiarity and immersion. The level seamlessly integrates with the game\'s overarching theme, ensuring a cohesive and engaging experience for players as they navigate through this relatable environment. The attention to detail and dedication to coherence in this design exemplify my passion for creating an exceptional gaming experience.'
    },
    {
        image: 'https://static.wixstatic.com/media/db664b_28382039a5e04e45882bc921fa8e42e1~mv2.png/v1/fill/w_615,h_346,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/Thumbnail%20Halloween%202022%20v6.png',
        title: 'Rendering: Blender Game Title Card',
        description: 'Employing Blender\'s powerful rendering capabilities, a captivating character is brought to life, fully immersed in the thrilling gameplay of a Halloween-themed update. The intricate design and skillful execution in this rendering showcase my ability to infuse festive elements seamlessly into the game world, promising an exciting and immersive experience for players during the seasonal update.'
    },
    {
        image: 'https://static.wixstatic.com/media/db664b_9df7cfcfbb604a03817b60df3da02e4b~mv2.png/v1/fill/w_615,h_346,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/trello2.png',
        title: 'Project Management: Trello Board',
        description: 'In the role of a hands-on manager, personally overseeing a small development team\'s workflow on Trello proves instrumental in orchestrating a seamless and productive collaboration. By adeptly utilizing issue-based task assignments, the team\'s progress is efficiently tracked, fostering clear communication and empowering each member to contribute effectively to the project\'s success.'
    },
    {
        image: 'https://static.wixstatic.com/media/db664b_3c9c977c81e44b1595376995fb2fc0eb~mv2.png/v1/fill/w_615,h_346,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/generator.png',
        title: 'Modeling: Blender Object Creation',
        description: 'Using Blender\'s versatile tools, I designed a visually striking gameplay prop in the form of an electrical box, boasting intricate details that seamlessly align with the game\'s overall theme. This meticulously designed object not only enhances the gaming environment with its recognizability but also contributes to the immersive gameplay experience, ensuring players feel fully engaged with the virtual world.'
    },
    // TBH, I don't think this belongs in the portfolio. It's a fun talking piece, but not really setting a professional tone.
    // {
    //     image: 'https://static.wixstatic.com/media/db664b_86bde35a6b9b43dfbc00ef556079984a~mv2.png/v1/fill/w_600,h_337,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/glitch.png',
    //     title: 'Abstract Art',
    //     description: 'An abstract piece of political theming'
    // }
]
</script>

<style scoped>
.background {
    background-image: url("https://www.toptal.com/designers/subtlepatterns/uploads/prism.png");
    background-repeat: repeat;
    background-blend-mode: darken;
}

.text-shadow {
    text-shadow: 1px 2px 2px black;
}
</style>

<style>
.v-carousel-item img {
    filter: none !important;
}
</style>
