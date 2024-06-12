<script setup lang="ts">
import { ref, onMounted } from 'vue';
import axios from 'axios';
import NewTask from '../components/NewTask.vue';
import Task from '../components/Task.vue';
import Modal from '../components/Modal.vue';

const tasks = ref<{ id: number; label: string }[]>([]);
const editingTask = ref<{ id: number; label: string } | null>(null);
const isEditModalOpen = ref<boolean>(false);

const fetchTasks = async () => {
  try {
    const response = await axios.get('http://127.0.0.1:8000/api/task');
    tasks.value = response.data.tasks;
  } catch (error) {
    alert('Erro ao buscar tarefas');
  }
};

const addTask = async (label: string) => {
  try {
    const response = await axios.post('http://127.0.0.1:8000/api/task', { task: label });
    const newTask = response.data.tasks;
    tasks.value.push(newTask);
  } catch (error) {
    alert('Erro ao adicionar a tarefa');
  }
};

const deleteTask = async (id: number) => {
  try {
    await axios.delete(`http://127.0.0.1:8000/api/task/${id}`);
    tasks.value = tasks.value.filter(task => task.id !== id);
  } catch (error) {
    alert('Erro ao deletar a tarefa');
  }
};

const changeTaskStatus = async (id: any, status: boolean) => {
  try {
    await axios.put(`http://127.0.0.1:8000/api/task/${id}`, {status: status});
    fetchTasks();
  } catch (error) {
    alert('Erro ao atualizar status');
  }
};

const openEditModal = (id: number) => {
  isEditModalOpen.value = true;
  const taskToEdit = tasks.value.find(task => task.id === id);
  if (taskToEdit) {
    editingTask.value = taskToEdit;
  }
};

const saveEditedTask = async () => {
  await axios.put(`http://127.0.0.1:8000/api/task/${editingTask.value.id}`, { task: editingTask.value.label });
  fetchTasks();
  closeEditModal();
};

const closeEditModal = () => {
  editingTask.value = null;
  isEditModalOpen.value = false;
};

 onMounted(fetchTasks);
</script>

<template>
  <main>
    <div class="container">
      <NewTask @task-added="addTask"/>
      <ul class="list">
        <Task
          v-for="task in tasks"
          :key="task.id"
          :id="task.id"
          :label="task.task"
          :status="task.status"
          @task-deleted="deleteTask"
          @edit-task="openEditModal(task.id)"
          @task-status="changeTaskStatus"
        />
      </ul>
    </div>
    <Modal
      :task="editingTask"
      :is-open="isEditModalOpen"
      @save="saveEditedTask"
      @close="closeEditModal"
    />
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
