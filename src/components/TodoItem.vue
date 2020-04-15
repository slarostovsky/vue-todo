<template>
  <div>
    <li>
      <span v-bind:class="{done: todo.completed}">
        <input type="checkbox" v-on:change="todo.completed = !todo.completed">
        <strong>{{ index+1 }}</strong>
        {{ todo.title | uppercase }}
      </span>
      <button 
      class="btn"
      v-on:click="$emit('remove-todo', todo.id)"
      >&times;</button>
    </li>
  </div>
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
      return value.toUpperCase()
    }
  }
};
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }

  input {
    margin-right: 1rem;
  }

  .btn{
    border-radius: 50%;
    border: none;
    background: red;
    color: white;
    font-weight: bold;
  }

  .done {
    color: gray;
    text-decoration: line-through;
  }
</style>