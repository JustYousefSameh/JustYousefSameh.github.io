<script setup lang="ts">
import { motion } from 'motion-v'
const infoItems = [
    "Yousef Sameh",
    "Software Engineer",
    "Egypt, Cairo"
];
</script>

<template>
    <motion.div class="welcome snap-center">
        <motion.img class="image" src="/aboutme/profile_photo.png" :initial='{ x: "-6em" }' :animate="{ x: '0em' }"
            :transition="{ duration: 0.5 }" />
        <div>
            <p v-for="(item, index) in infoItems" :key="index" class="text-item"
                :style="{ animationDelay: `${index * 0.3}s` }">
                {{ item }}
            </p>
        </div>
    </motion.div>
</template>

<style scoped>
.text-item {
    opacity: 0;
    animation: fade-slide-up 0.6s ease forwards;
    font-size: 2rem;
    color: #e5e7eb;
    /* Tailwind's text-gray-200 */
}

.text-item:first-child {
    font-weight: 600;
    font-size: 3rem;
    /* Tailwind's text-5xl */
}

/* Optional if you want to animate from the bottom */
@keyframes fade-slide-up {
    from {
        opacity: 0;
        transform: translateY(20px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.image {
    border-radius: 15px;
    height: 66%;
}

@keyframes slide-in-to-right {
    from {
        opacity: 0;
        transform: translateX(-100%);
    }

    to {
        opacity: 1;
        transform: translateX(0px);
    }
}

@keyframes slide-in-to-left {
    from {
        opacity: 0;
        transform: translateX(200%);
    }

    to {
        opacity: 1;
        transform: translateX(0px);
    }

}


.welcome {
    display: flex;
    gap: 8em;
    height: 100vh;
    align-items: center;
    justify-content: center;
}

@keyframes popin {
    from {
        scale: 0.8;
    }

    to {
        scale: 1;
    }
}
</style>
