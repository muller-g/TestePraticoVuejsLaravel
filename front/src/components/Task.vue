<template>
  <li class="task">
    <input type="checkbox" name="task" id="task" @change="toggleTextDecoration" v-model="isChecked">
    <span :class="{ 'completed-task': isChecked }">{{ label }}</span>
    <button @click="openEditModal">Edit</button>
    <button @click="deleteTask">Delete</button>
  </li>
</template>

<script>
export default {
  name: 'Task',
  props: {
    id: {
      type: Number,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    status: {
      type: Number,
      required: true
    }
  },
  computed: {
    isChecked: {
      get() {
        return this.status === 1;
      },
      set(checked) {
        this.$emit('task-status', this.id, checked ? 1 : 0);
      }
    }
  },
  methods: {
    openEditModal() {
      this.$emit('edit-task', this.id);
    },
    deleteTask() {
      this.$emit('task-deleted', this.id);
    },
  }
};
</script>

<style scoped>
.task {
  width: 100%;
  display: flex;
  gap: 10px;
  align-items: center;
}

.task input {
  max-width: 20px;
  width: 100%;
  cursor: pointer;
}

.task span {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 100%;
  transition: text-decoration .3s, opacity .3s;
}

.task button {
  padding: 5px;
  background-color: #5A94FF;
  color: #fff;
  outline: none;
  border: 0;
  border-radius: 6px;
  cursor: pointer;
}

.task button:last-child {
  background-color: #FE5D5A;
  transition: .3s;
}

.task button:hover {
  transition: .3s;
  opacity: .7;
}

.completed-task {
  text-decoration: line-through;
  opacity: 0.7;
}
</style>
