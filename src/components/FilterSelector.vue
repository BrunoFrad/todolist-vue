<script setup lang="ts">
    import {
        Select,
        SelectContent,
        SelectItem,
        SelectTrigger,
        SelectValue,
    } from '@/components/ui/select';
    import { ref, defineExpose } from 'vue';

    const currentFilter = ref("");

    defineExpose( currentFilter );

</script>

<template>
    <Select v-model="currentFilter">
            <SelectTrigger class="w-2/4">
                <SelectValue placeholder="Filter" />
            </SelectTrigger>
            <SelectContent>
                <SelectItem value="none">None</SelectItem>
                <SelectItem value="purple">
                    <svg height="5" width="5" xmlns="http://www.w3.org/2000/svg">
                        <circle r="5" cx="5" cy="8" fill="purple" />
                    </svg> 
                    Purple
                </SelectItem>
                <SelectItem value="red">
                    <svg height="5" width="5" xmlns="http://www.w3.org/2000/svg">
                        <circle r="5" cx="5" cy="8" fill="red" />
                    </svg> 
                    Red
                </SelectItem>
                <SelectItem value="cyan">
                    <svg height="5" width="5" xmlns="http://www.w3.org/2000/svg">
                        <circle r="5" cx="5" cy="8" fill="cyan" />
                    </svg> 
                    Blue
                </SelectItem>

                <SelectItem value="lime">
                    <svg height="5" width="5" xmlns="http://www.w3.org/2000/svg">
                        <circle r="5" cx="5" cy="8" fill="lime" />
                    </svg> 
                    Green
                </SelectItem>

            </SelectContent>
        </Select>
</template>