<template>
  <div>
    <h1>{{ msg }}</h1>
    <counter />
    <todo-list />
  </div>
</template>

<script>
import TodoList from "./TodoList.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    TodoList
  }
};
</script>