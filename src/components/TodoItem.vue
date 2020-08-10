<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input 
        type="checkbox" 
        v-on:change="todo.completed = !todo.completed"
        v-bind:id="'item-' + index"
        v-bind:checked="todo.completed"
      >
      <label v-bind:for="'item-' + index">
        {{ index + 1 }}.
        {{ todo.title | uppercase}}
      </label>
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      },
      index: Number
    },
    filters: {
      uppercase(value) {
        return value.toUpperCase();
      }
    }
  }
</script>

<style scoped>
  li {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
    padding: 0.5rem 2rem;
    border: 1px solid #ccc;
  }

  input {
    margin-right: 1rem;
  }

  .rm {
    background-color: red;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
  }

  .done {
    text-decoration: line-through;
  }
</style>