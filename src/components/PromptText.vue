<template>
    <div class="container">
        <h1>
            <span class="text">{{ animatedText }}</span><span class="blink">_</span>
        </h1>
    </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, defineProps } from 'vue';

const props = defineProps({
    text: String
});

const animatedText = ref("");
const typingSpeed = 150;
let typingInterval = null;

const typeText = (text) => {
    let i = 0;
    typingInterval = setInterval(() => {
        if (i < text.length) {
            animatedText.value += text.charAt(i);
            i++;
        } else {
            clearInterval(typingInterval);
        }
    }, typingSpeed);
};

onMounted(() => {
    const text = props.text || "";
    typeText(text);
});

onBeforeUnmount(() => {
    clearInterval(typingInterval);
});
</script>

<style>
.container {
    display: flex;
    color: white;
    font-family:'Roboto Mono';
}

.blink {
    padding-left: 0;
    animation: blink-animation 1s infinite;
}

.text {
    white-space: pre;
    text-align: center;
}

@keyframes blink-animation {
  0% { opacity: 1; }
  50% { opacity: 0; }
  100% { opacity: 1; }
}
</style>
