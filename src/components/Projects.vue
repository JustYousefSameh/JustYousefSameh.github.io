<script setup lang="ts">
import { ref } from 'vue'
import { motion } from 'motion-v'

const projectsData = [
    {
        name: "TalkU",
        img: ["/TalkU.gif"]
    },
    {
        name: "GPA Calculator",
        img: ["/GPA_LIGHT.jpg", "/GPA_DARK.jpg"]
    },
    {
        name: "Master Courses",
        img: ["/GPA_DARK.png"]
    }
];


const hoveredIndex = ref()

function getFloatStyle() {
    const offset = Math.floor((Math.random() - 0.5) * 10) //adding an offset 
    const range = Math.floor(Math.random() * 10 + 10 + offset) // 10–20px
    const duration = (Math.random() * 1.5 + 2.5).toFixed(2) // 2.5–4s

    return {
        '--float-range': `${range}px`,
        animationDuration: `${duration}s`
    }
}

function onMouseLeave(index: number) {
    if (index == hoveredIndex.value) {
        hoveredIndex.value = undefined;
    }
}
</script>


<template>
    <div class="flex justify-start items-end gap-30 h-screen snap-center">
        <div class="project-showcase">
            <transition name="project-image-fade" mode="out-in">
                <div v-if="hoveredIndex !== null && hoveredIndex !== undefined"
                    class="flex gap-4 h-[75vh] justify-center items-center">
                    <img v-for="item in projectsData[hoveredIndex].img" :key="item" class="project-image"
                        :src="'/aboutme' + item" :style="getFloatStyle()" />
                </div>
            </transition>
        </div>
        <motion.div class="h-[90vh] flex-2" :initial="{ opacity: 0 }" :whileInView="{ opacity: 1 }"
            :transition="{ duration: 1 }">
            <p class="pb-8 font-black text-6xl">
                Projects
            </p>
            <div class="project-list">
                <div v-for="(item, index) in projectsData" :key="index" @mouseenter="hoveredIndex = index"
                    @mouseleave="onMouseLeave(index)" class="project-item">
                    <font-awesome-icon :icon="['fas', 'arrow-right']" class="arrow" />
                    <div class="name">
                        {{ item.name }}
                    </div>
                </div>
            </div>
        </motion.div>
    </div>
</template>

<style scoped>
.project-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.project-item {
    display: flex;
    font-size: 29px;
    font-weight: 500;
    align-items: center;
    position: relative;
    cursor: pointer;
    overflow: hidden;
}

/* Arrow hidden and moved left by default */
.arrow {
    opacity: 0;
    transform: translateX(-10px);
    transition: all 0.3s ease;
    margin-right: 8px;
    width: 20px;
    position: absolute;
    left: 0;
}

/* Name has a transition and initial padding to keep layout consistent */
.name {
    transition: transform 0.3s ease;
    transform: translateX(-20px);
    padding-left: 20px;
}

/* On hover: show arrow and move text */
.project-item:hover .arrow {
    opacity: 1;
    transform: translateX(0);
}

.project-item:hover .name {
    transform: translateX(10px);
}

.project-showcase {
    flex: 3;
    gap: 2vh;
    padding: 8vh;
    /* position: relative; */
}

@keyframes float {
    from {
        transform: translateY(calc(var(--float-range, 10vh) * -1));
    }

    to {
        transform: translateY(var(--float-range, 10vh));
    }
}

.project-image {
    max-height: 85vh;
    border-radius: 20px;
    object-fit: cover;

    /* Floating card animation */
    animation-name: float;
    animation-iteration-count: infinite;
    animation-direction: alternate;

    /* Glass card style */
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border: 1px solid rgba(255, 255, 255, 0.2);

    /* Glow and shadow */
    /* box-shadow: */
    /*     0 15px 35px rgba(0, 255, 255, 0.2), */
    /*     0 0 20px rgba(0, 255, 255, 0.3), */
    /*     inset 0 0 10px rgba(255, 255, 255, 0.05); */

    transition: transform 0.3s ease, box-shadow 0.3s ease;
}


.project-image-fade-enter-active,
.project-image-fade-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
}

.project-image-fade-enter-from {
    opacity: 0;
    transform: translateX(-20px);

}

.project-image-fade-leave-to {
    opacity: 0;
    transform: translateX(20px);
}
</style>
