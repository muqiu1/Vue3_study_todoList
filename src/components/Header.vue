<template>
  <div class="todo-header">
    <input
      type="text"
      placeholder="请输入你的任务名称"
      v-model="title"
      @keyup.enter="add"
    />
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "myHeader",
  props: {
    addTodo: {
      type: Function,
      required: true,
    },
  },
  setup(props) {
    const title = ref("");

    const add = () => {
      const text = title.value;
      if (!text.trim()) return;
      const todo = {
        id: Date.now(),
        title: text,
        isChecked: false,
      };

      props.addTodo(todo);

      title.value = "";
    };

    return {
      title,
      add,
    };
  },
});
</script>