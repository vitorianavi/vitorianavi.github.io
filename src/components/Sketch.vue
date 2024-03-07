<script setup lang="ts">
import { ref, onMounted,  onUnmounted } from "vue"
import p5 from "p5"

const canvas = ref()

onMounted(() => {
    let num = 2000;
    let range = 20;

    let ax = [];
    let ay = [];

    let currentVisibleTop;
    let currentVisibleBottom;

    const sketch = (p5) => {
        p5.setup = () => {
            let canvasWidth = p5.windowWidth;
            let canvasHeight = p5.windowHeight*4;
            p5.createCanvas(canvasWidth, canvasHeight);
            for ( let i = 0; i < num; i++ ) {
                ax[i] = canvasWidth / 2;
                ay[i] = p5.windowHeight / 2;
            }
            p5.frameRate(15);
        }

        p5.draw = () => {
            // Shift all elements 1 place to the left
            for ( let i = 1; i < num; i++ ) {
                ax[i - 1] = ax[i];
                ay[i - 1] = ay[i];
            }

            // Put a new value at the end of the array
            ax[num - 1] += p5.random(-range, range);
            ay[num - 1] += p5.random(-range, range);

            let visibleTop = p5.max(0, window.scrollY);
            let visibleBottom = window.scrollY + p5.windowHeight;

            // Constrain all points to the visible screen
            ax[num - 1] = p5.constrain(ax[num - 1], 0, p5.windowWidth);
            ay[num - 1] = p5.constrain(ay[num - 1], visibleTop, visibleBottom);

            // Draw a line connecting the points
            for ( let j = 1; j < num; j++ ) {
                let val = j / num * 204.0 + 51;
                p5.strokeWeight(3);
                p5.stroke(val);
                p5.line(ax[j - 1], ay[j - 1], ax[j], ay[j]);
            }
        }
    }
    const newP5 = new p5(sketch, canvas.value);
})
</script>

<template>
  <div ref="canvas"></div>
</template>
