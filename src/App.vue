<script setup lang="ts">
import Welcome from './components/Welcome.vue'
import Projects from './components/Projects.vue';
import Hello from './components/Hello.vue';
</script>
<template>
    <div class="main snap-y snap-mandatory">
        <Welcome />
        <Projects />
    </div>
</template>

<style scoped>
.main {
    scroll-snap-type: y mandatory;
    background-color: #161616;
    opacity: 1;
    background-image: radial-gradient(#3d3d3d 2px, #161616 2px);
    background-size: 40px 40px;
}
</style>

<style module>
html {
    scrollbar-width: none;
}
</style>
