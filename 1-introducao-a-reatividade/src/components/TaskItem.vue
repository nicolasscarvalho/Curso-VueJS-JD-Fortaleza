<script setup lang="ts">
    import Button from 'primevue/button';
    const props = defineProps({
        taskName: String,
        taskIndex: Number,
        deleteTask: Function
    })
</script>

<template>
    <div class="task-item">
        <p>{{ taskName }}</p>
        <Button icon="pi pi-trash" severity="danger" rounded @click="() => deleteTask(taskIndex)" />
    </div>
</template>

<style scoped>
    .task-item {
        display: flex;
        align-items: center;
        justify-content: space-between;
        box-shadow: 0px 5px 5px 0px #059669;
        width: 550px;
        padding: 0px 10px;
        margin-bottom: 20px;
        border-radius: 10px;
    }
</style>