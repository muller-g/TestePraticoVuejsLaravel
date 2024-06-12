<template>
  <div class="modal" v-if="isOpen">
    <div class="modal-content">
      <h2>Editar Tarefa</h2>
      <input type="text" v-model="task.label">
      <button @click="save">Salvar</button>
      <button @click="close">Cancelar</button>
    </div>
  </div>
</template>

<script>
  export default {
     props: {
       task: {
         type: Object,
         default: null
       },
       isOpen: {
         type: Boolean,
         default: false
       }
     },
     methods: {
       save() {
         this.$emit('save');
       },
       close() {
         this.$emit('close');
       }
     }
  };
</script>

<style scoped>
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal .modal-content h2 {
    font-size: 16px;
    margin-bottom: 5px;
  }

  .modal-content {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
  }

  .modal input {
    width: 100%;
    outline: none;
    border: 0px;
    border-bottom: 1px solid black;
    background-color: unset;
    font-size: 14px;
    padding: 5px;
    margin-bottom: 10px;
  }

  .modal button {
    background-color: #5A94FF;
    outline: none;
    color: #fff;
    border: 0;
    border-radius: 6px;
    padding: 5px 20px;
    cursor: pointer;
    font-size: 16px;
    transition: .3s;
    margin-right: 10px;
  }   

  .modal button:last-child {
    background-color: #FE5D5A;
    transition: .3s;
  }

  .modal button:hover {
    transition: .3s;
    opacity: .7;
  }
</style>