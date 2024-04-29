<script setup lang="ts">

  import { ref } from 'vue';
  import TaskItem from './components/TaskItem.vue';
  import InputText from 'primevue/inputtext';
  import Button from 'primevue/button';

  interface TaskModel {
    taskName: String,
    taskIndex: Number
  }

  const newTaskName = ref<String>("")
  const taskList = ref< TaskModel[] >([])

  const date = new Date()
  const months = ["Janeiro", "Fevereiro", "Março", "Abril", "Maio", "Junho", "Julho", "Outubro", "Novembro", "Dezembro"]

  const addNewTask = ()=>{
    taskList.value.push({
      taskName: newTaskName.value,
      taskIndex: taskList.value.length
    })
  }

  const deleteTask = (index)=> {
    taskList.value.splice(index,1)
  }

</script>

<template>

  <div class="to-do-app">
    <div class="header">
      <h1>{{ date.getUTCDate() }} de {{ months[date.getUTCMonth()-1] }}, {{ date.getUTCFullYear() }}</h1>
        <section>
          <InputText type="text" placeholder="Título da nota" v-model="newTaskName"/>
          <Button icon="pi pi-plus" severity="sucess" rounded @click="addNewTask" />
        </section>
    </div>

    <div class="task-list">
      <TaskItem v-for="(item, index) in taskList" :key="index" :deleteTask="deleteTask" :taskName="item.taskName" :taskIndex="index"/>
    </div>
  </div>

</template>

<style scoped>
  .to-do-app {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 100px;
  }

  .to-do-app section {
    display: flex;
    width: 100%;
    justify-content: space-between;
  }
</style>
