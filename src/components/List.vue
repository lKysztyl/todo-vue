<script setup>
    const props = defineProps(['tasks'])
</script>

<template>
    <ul class="list-group mt-4">
        <li class="list-group-item" v-for="tasks in props.tasks">
            <input @change="evento => tasks.finalizada = evento.target.checked" :checked="tasks.finalizada"
                :id="tasks.titulo" type="checkbox">
            <label :class="{ done: tasks.finalizada }" class="ms-3" :for="tasks.titulo">
                {{ tasks.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>