<script setup lang="ts">
    import AddTask from '@/components/Add-Task.vue';
    import TasksTable from '@/components/TasksTable.vue';
    import { ref } from 'vue';

    const tasksController = ref<TaskType[]>([]);

    function handleStorage(tasks: TaskType[]) {
        tasksController.value = tasks;
    }

</script>

<template>
    <main class="flex flex-col items-center justify-center h-[80vh] gap-[3vh] lg:gap-[3vw]">
        <TasksTable :tasks="tasksController" />
        <AddTask @taskStorage="handleStorage" />
    </main>
</template>