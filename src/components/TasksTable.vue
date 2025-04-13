<script setup lang="ts">
    import { onMounted, ref } from 'vue';
    
    const tasksStored = ref<string | null>(null);

    onMounted(() => {
        tasksStored.value = localStorage.getItem("tasks");
    });

</script>

<template>

    <h1 v-if="tasksStored == null" className="text-neutral-700 text-center text-5xl font-bold">
        No More Tasks 😄
    </h1>

    <h1 v-else>Tasks...</h1>

</template>