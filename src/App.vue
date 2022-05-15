<template>
  <div class="todo-container">
    <div class="todo-warp">
      <myHeader :addTodo="addTodo" />
      <myList :todos="todos" />
      <myFooter />
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, reactive, toRefs } from "vue";

import { Todo } from "./types/todo";

import myFooter from "./components/Footer.vue";
import myList from "./components/List.vue";
import myHeader from "./components/Header.vue";
export default defineComponent({
  name: "App",
  components: {
    myHeader,
    myList,
    myFooter,
  },
  setup() {
    const state = reactive<{ todos: Todo[] }>({
      todos: [
        { id: 1, title: "123414", isChecked: false },
        { id: 2, title: "123414", isChecked: false },
        { id: 3, title: "123414", isChecked: false },
      ],
    });

    const addTodo = (todo:Todo) => {
      state.todos.unshift(todo);
    }

    return {
      ...toRefs(state),
      addTodo,
    };
  },
});
</script>
<style>
.todo-container {
  width: 600px;
  margin: 0 auto;
}

.todo-container .todo-warp {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>