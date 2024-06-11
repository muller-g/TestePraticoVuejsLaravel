<template>
    <button :class="buttonClass" @click="handleClick">
      {{ label }}
    </button>
  </template>
  
  <script>
  export default {
    name: 'ButtonComponent',
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
  .btn {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
  }
  
  .btn-primary {
    background-color: #007bff;
    color: white;
  }
  
  .btn-secondary {
    background-color: #6c757d;
    color: white;
  }
  </style>
  