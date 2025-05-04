<script setup lang="ts">
import { onMounted, ref } from 'vue';


const textList = [
    'Welcome to my portfolio',
    'Sit back and watch',
    "Don't touch anything or it will break :)",
]

let index = 0;
const text = ref(textList[index]);

onMounted(() => {
    let intervalID = setInterval(() => {
        if (index == 2) {
            clearInterval(intervalID)
            return;
        }
        index++
        text.value = textList[index];
    }, 3000);
})

</script>

<template>
    <div class="hello">
        <div class="typewriter">
            <p class="text">
                {{ text }}
            </p>
        </div>
    </div>
</template>

<style scoped>
.fadeout-leave-active {
    animation-duration: 2s;
}


.fadeout-leave-from {
    opacity: 1;
}

.fadeout-leave-to {
    opacity: 0;
}

.hello {
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    background-color: #121212;
    z-index: 999;
}

.typewriter {
    display: inline-block;
}

.typewriter .text {
    font-size: 3em;
    overflow: hidden;
    /* Ensures the content is not revealed until the animation */
    border-right: .15em solid orange;
    /* The typwriter cursor */
    white-space: nowrap;
    /* Keeps the content on a single line */
    margin: 0 auto;
    /* Gives that scrolling effect as the typing happens */
    letter-spacing: .15em;
    /* Adjust as needed */
    animation:
        typing 3.0s ease-in-out infinite,
        blink-caret .75s step-end infinite;
}

@keyframes fade-out {
    from {
        opacity: 1;
    }

    to {
        opacity: 0;
    }
}

@keyframes typing {
    0% {
        width: 0
    }

    66% {
        width: 100%
    }

    100% {
        width: 100%
    }
}

/* The typewriter cursor effect */
@keyframes blink-caret {

    from,
    to {
        border-color: transparent
    }

    50% {
        border-color: orange;
    }
}
</style>
