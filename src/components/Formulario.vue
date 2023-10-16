<script setup>
    const props = defineProps(['cadastraTask', 'taskTemp', 'switchFilter', 'editaTaskTemp'])
</script>

<template>
    <form @submit.prevent="props.cadastraTask">
        <div class="row">
            <div class="col">
                <input class="form-control" @change="props.editaTaskTemp" required :value="props.taskTemp" type="text" placeholder="Digite suas tarefas">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Adicionar</button>
            </div>
            <div class="col-md-2">
                <select @change="props.switchFilter" class="form-control">
                    <option value="todas">All Tasks</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>