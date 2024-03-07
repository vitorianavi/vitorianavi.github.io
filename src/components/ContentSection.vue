<template>
    <div class="section">
        <PromptText class="title" :text="sectionTitleText"/>
        <div class="content">
            <div class="img imgLeft" :style="{ backgroundImage: `url('${imgLeftPath}')` }"></div>
            <div class="img imgRight" :style="{ backgroundImage: `url('${imgRightPath}')` }"></div>
        </div>
    </div>
</template>

<script setup>
import { ref, defineProps } from 'vue';
import PromptText from "./PromptText.vue";

const props = defineProps({
    imgLeftPath: String,
    imgRightPath: String,
    sectionTitleText: String
});

</script>

<style scoped>
.title {
    margin-top: 0;
    padding-top: 4vw;
    font-size: 1.3vw;
}

.content {
    margin: 8vh 0 0 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 50px;
    width: 90vw;
    height: 100vh;
}

.img{
    background-repeat: no-repeat;
    background-size: contain;
    filter: grayscale(20);
    transition: filter 0.5s ease;
}

.img:hover {
    filter: grayscale(0);
    cursor: pointer;
}

.imgRight {
    margin-top: 10vh;
}

</style>
