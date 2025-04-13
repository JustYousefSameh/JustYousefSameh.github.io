<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
</script>

<template>
    <div class="flex flex-col justify-self-auto space-y-3">
        <h1 class="text-white text-3x1 font-bold underline">{{ msg }}</h1>
        <button class="border-2 border-solid border-yellow-50 p-3 rounded-sm hover:border-blue-950" type="button"
            @click="count++">
            count is {{ count }}
        </button>
        <p class="text-white">
            Edit
            <code>components/HelloWorld.vue</code> to test HMR
        </p>
        <p>
            Check out
            <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue +
            Vite
            starter
        </p>
        <p>
            Learn more about IDE Support for Vue in the
            <a href="https://vuejs.org/guide/scaling-up/tooling.html#ide-support" target="_blank">Vue Docs Scaling up
                Guide</a>.
        </p>
        <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>


    </div>
</template>

<style scoped>
.read-the-docs {
    color: #888;
}
</style>
