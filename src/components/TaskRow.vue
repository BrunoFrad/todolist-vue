<script setup lang="ts">
    import { defineProps } from 'vue';
    import { TableRow, TableCell } from './ui/table';
    import { Checkbox } from './ui/checkbox';
    import { Button } from './ui/button';

    defineProps<{taskList : TaskType[]}>();

</script>

<template>
    <TableRow v-for="task in taskList" :key="task.name">
        <TableCell>
            <svg height="11" width="10" xmlns="http://www.w3.org/2000/svg">
                <circle r="5" cx="5" cy="5" :fill="task.filter" />
            </svg>
        </TableCell>
        <TableCell>
            {{ task.name }}
        </TableCell>
        <TableCell>
            <Checkbox :model-value="task.done" @click="task.done = !task.done" />
        </TableCell>
        <TableCell class="text-right">
            <Button @click="$emit('deleteTask', task.name)">
                Delete
            </Button>
        </TableCell>
    </TableRow>
</template>