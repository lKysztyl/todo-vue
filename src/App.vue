<script setup>
  import { reactive } from 'vue';
  import Header from './components/Header.vue';
  import Formulario from './components/Formulario.vue';
  import List from './components/List.vue';

  const state = reactive({
    filtro: 'todas',
    taskTemp: '',
    tasks: [
      {
        titulo: 'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar Typescript',
        finalizada: false,
      },
      {
        titulo: 'Estuda SASS',
        finalizada: true,
      }
    ]
  })

  const getTaskPending = () => {
    return state.tasks.filter(tasks => !tasks.finalizada)
  }

  const getTasksFinished = () => {
    return state.tasks.filter(tasks => tasks.finalizada)
  }

  const getTasksFiltered = () => {
    const {filtro} = state;
    
    switch (filtro) {
      case 'pendentes':
        return getTaskPending();

      case 'finalizadas':
        return getTasksFinished();
    
      default:
        return state.tasks;
    }
  }

  const cadastraTask = () => {
    const newTask = {
      titulo: state.taskTemp,
      finalizada: false,
    }
    state.tasks.push(newTask);
    state.taskTemp = '';
  }
</script>

<template>
  <div class="container">
    <Header :task-pending="getTaskPending().length"/>
    <Formulario :switch-filter="evento => state.filtro = evento.target.value" :task-temp="state.taskTemp" :edita-task-temp="evento => state.taskTemp = evento.target.value" :cadastra-task="cadastraTask"/>
    <List :tasks="getTasksFiltered()"/>
  </div>
</template>