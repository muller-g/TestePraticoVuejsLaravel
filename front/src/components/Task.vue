<template>
  <li class="task">
    <input type="checkbox" name="task" id="task">
    <span>{{ label }}</span>
    <button>Edit</button>
    <button>Delete</button>
  </li>
</template>
  
<script>
  export default {
    name: 'Task',
    props: {
      label: {
        type: String,
        required: true
      },
      type: {
        type: String,
        default: 'button'
      },
      variant: {
        type: String,
        default: 'primary'
      }
    },
    computed: {
      buttonClass() {
        return `btn btn-${this.variant}`;
      }
    },
    methods: {
      handleClick(event) {
        this.$emit('click', event);
      }
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
</style>
  