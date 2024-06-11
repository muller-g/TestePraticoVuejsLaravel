<template>
    <div class="wrapper">
        <input type="text" placeholder="Nova tarefa" v-model="text"/>
        <button :class="buttonClass" @click="handleClick">+</button>
    </div>
</template>
  
<script>
  export default {
    name: 'NewTask',
    computed: {
      buttonClass() {
        return `btn btn-${this.variant}`;
      }
    },
    methods: {
      handleClick(event) {
        alert(this.text)
        this.$emit('click', event);
      }
    }
  };
</script>
  
<style scoped>
    .wrapper {
        width: 100%;
        display: flex;
        gap: 10px;
    }

    .wrapper input {
        width: 100%;
        outline: none;
        border: 0px;
        border-bottom: 1px solid black;
        background-color: unset;
        font-size: 14px;
        padding: 5px;
    }

    .wrapper button {
        background-color: #5A94FF;
        outline: none;
        color: #fff;
        border: 0;
        border-radius: 6px;
        padding: 0 20px;
        cursor: pointer;
        font-weight: bold;
        font-size: 16px;
        transition: .3s;
    }

    .wrapper button:hover {
        background-color: #5a94ff9c;
        transition: .3s;
    }
</style>
  