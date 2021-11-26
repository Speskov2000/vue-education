<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" 
        @change="todo.completed = !todo.completed">
      <strong>{{todo.id}}</strong>
      {{ uppercase }}
    </span>
    <button class="rm" 
      @click="$emit('remove-todo', todo.id)">
      &times;
    </button>
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
  computed: {
    uppercase() {
      return this.todo.title.charAt(0).toUpperCase()
      + this.todo.title.slice(1)
    }
  }
}
</script>


<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }

  .rm {
    background: red;
    color: #fff;
    font-weight: bold;
  }

  input {
    margin-right:  1rem;
  }

  .done {
    text-decoration: line-through;
  }
</style>
