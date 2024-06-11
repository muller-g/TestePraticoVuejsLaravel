<script setup lang="ts">
import NewTask from '../components/NewTask.vue';
import Task from '../components/Task.vue';
</script>

<template>
  <main>
    <div class="container">
      <NewTask/>
      <ul class="list">
        <Task label="Tarefa 1"/>
        <Task label="Tarefa 2"/>
        <Task label="Tarefa 3"/>
        <Task label="Tarefa 4"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
        <Task label="Tarefa 5"/>
      </ul>
    </div>
  </main>
</template>

<style scoped>
  main {
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #5A94FF;
  }

  .container {
    width: 600px;
    height: 700px;
    display: flex;
    flex-direction: column;
    background-color: #F0F8FB;
    border-radius: 20px;
    padding: 30px;
  }

  .list {
    list-style: none;
    width: 100%;
    height: 100%;
    max-height: 600px;
    overflow-y: scroll;
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-top: 30px;
    padding-right: 10px;
  }

  ::-webkit-scrollbar {
    width: 10px;
    height: 10px;
  }

  ::-webkit-scrollbar-thumb {
    background-color: #5A94FF;
    border-radius: 5px;
  }

  ::-webkit-scrollbar-track {
    background: unset;
  }
</style>