<script setup lang="ts">
    import { onMounted, ref, defineProps, watch } from 'vue';
    
    const tasksStored = ref<string | null>(null);
    let newTasks: TaskType[] = []
    
    const props = defineProps({
        tasks: {
            type: Array as () => TaskType[],
            required: true,
        }
    });

    onMounted(() => {
        tasksStored.value = localStorage.getItem("tasks");
        if (tasksStored.value)
            newTasks = JSON.parse(tasksStored.value);

    });

    watch(props, (newProps) => {
        newProps.tasks.forEach((el) => {
            newTasks.push(el);
        });
    })

</script>

<template>

    <h1 v-if="newTasks.length === 0" className="text-neutral-700 text-center text-5xl font-bold">
        No More Tasks 😄
    </h1>

    <h1 v-else>Tasks...</h1>

</template>