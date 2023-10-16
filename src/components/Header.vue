<script setup>
    const props = defineProps(['taskPending'])
</script>

<template>
    <header class="p-5 mb-4 mt-4 rounded-3">
        <h1>Minhas tarefas</h1>
        <p>
            Você possui <span>{{ props.taskPending }}</span> tarefas pendentes
        </p>
    </header>
</template>

<style scoped>
    header {
        background-color: #4DB6AC;
        color: #FFF;
    }
</style>