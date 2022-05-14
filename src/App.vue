<template>
    <div class="todo-container">
        <div class="todo-warp">
            <myHeader />
            <myList />
            <myFooter />
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

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