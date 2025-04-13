<script setup lang="ts">
    import { Input } from '@/components/ui/input';
    import { Button } from '@/components/ui/button';
    import FilterSelector from '@/components/FilterSelector.vue';
</script>

<template>
    <section class="flex w-5/6 lg:w-lg items-center gap-1.5">
        <Input type="text" placeholder="Type your new task" />
        <FilterSelector />
        <Button>
            Send
        </Button>
    </section>
</template>