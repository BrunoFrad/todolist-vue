<script setup lang="ts">
    import AddTask from '@/components/Add-Task.vue';
    import TasksTable from '@/components/TasksTable.vue';
    import { ref, computed, watch } from 'vue';

    const tasksArr = ref<TaskType[]>([]);

    const storedTasks = localStorage.getItem("tasks");
    if (storedTasks != null) {
        tasksArr.value = JSON.parse(storedTasks);
    }

    watch(tasksArr, (newVal) => {
        localStorage.setItem("tasks", JSON.stringify(newVal));
    }, { deep: true });

    const getGap = computed(() => {
        if (window.innerWidth >= 1024)
            return `${(tasksArr.value.length * 5) + 6}vh`;
        else
            return `${(tasksArr.value.length) + 6}vw`;
    });

    function handleStorage(task: TaskType) {
        tasksArr.value.push(task);
    }

</script>

<template>
    <main
        class="flex flex-col items-center justify-center h-[80vh]"
        :style="{ gap: getGap }"
    >
        <TasksTable :tasks="tasksArr" />
        <AddTask @taskStorage="handleStorage" />
    </main>
</template>