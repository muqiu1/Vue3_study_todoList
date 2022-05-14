<template>
  <ul class="todo-main">
      <myItem />
  </ul>
</template>
<script lang="ts">
import { defineComponent } from "vue";

import myItem from "./Item.vue";
export default defineComponent({
  name: "myList",
  components: {
    myItem,
  },
});
</script>
<style>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>