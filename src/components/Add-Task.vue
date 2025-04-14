<script setup lang="ts">
    import { Input } from '@/components/ui/input';
    import { Button } from '@/components/ui/button';
    import FilterSelector from '@/components/FilterSelector.vue';
    import { ref, defineEmits } from 'vue';

    const inputText = ref(""); // Text from the Input of Tasks
    const filterComponent = ref<typeof FilterSelector | null>(null); // Reference of the FilterSelectorComponent
    const emit = defineEmits(); // Event Emitter

    function handleSubmit() {
        const storedTasks: string | null = localStorage.getItem("tasks"); // Get the current tasks in localStorage
        let taskArr: TaskType[] = []; // Array to be stored

        if (storedTasks != null)
            taskArr = JSON.parse(storedTasks);

        if (taskArr?.length <= 9) {
            const newTask: TaskType = { // New task with the info from the input
                name: inputText.value,
                filter: filterComponent.value,
                done: false,
            }

            taskArr.push(newTask);

            localStorage.setItem("tasks", JSON.stringify(taskArr));

            emit("taskStorage", taskArr.pop());
        }

        inputText.value = "";
        filterComponent.value = null;
    }

</script>

<template>
    <section class="flex w-5/6 lg:w-3/6 items-center gap-1.5">
        <Input type="text" placeholder="Type your new task" v-model="inputText" />
        <FilterSelector v-model="filterComponent" />
        <Button @click="handleSubmit">
            Send
        </Button>
    </section>
</template>