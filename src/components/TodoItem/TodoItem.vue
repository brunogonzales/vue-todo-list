<template>
  <p :class="{'is-complete': completed}">
    <input type="checkbox" :checked="completed" @change="markComplete" />
    {{todo.title}}
    <button @click="$emit('del-todo', todo.id)" class="del">x</button>
  </p>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return {
      completed: this.todo.completed
    };
  },
  methods: {
    markComplete() {
      this.completed = !this.completed;
    }
  }
};
</script>

<style scoped>
.is-complete {
  text-decoration: line-through;
}

.del {
  background: red;
  padding: 5px;
}
</style>