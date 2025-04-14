<script setup lang="ts">
    import { ref, defineProps, watch } from 'vue';
    import { Table, TableBody } from './ui/table';
    import TaskRow from './TaskRow.vue';

    const newTasks = ref<TaskType[]>([])
    
    const props = defineProps({
        tasks: {
            type: Array as () => TaskType[],
            required: true,
        }
    });

    newTasks.value = props.tasks;

    function handleDelete(taskName: string) {
        for(let i = 0; i < newTasks.value.length; i++) {
            if (newTasks.value[i].name === taskName)
                newTasks.value.splice(i, 1);
        }
    }

    watch(newTasks, (updatedTasks) => {
        localStorage.setItem("tasks", JSON.stringify(updatedTasks));
    });

</script>

<template>

    <h1 v-if="newTasks.length === 0" className="text-neutral-700 text-center text-5xl font-bold">
        No More Tasks 😄
    </h1>

    <section v-else class="rounded w-[70vw] lg:w-[45vw] lg:h-[6vh] sm:h[3vh]">
        <Table class="border">
            <TableBody>
                <TaskRow :taskList="newTasks" @deleteTask="handleDelete" />
            </TableBody>
        </Table>
    </section>

</template>