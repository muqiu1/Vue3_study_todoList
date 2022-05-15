<template>
  <li
    @mouseenter="mousehandler(true)"
    @mouseleave="mousehandler(false)"
    :style="{ backgroundColor: bgColor, color: myColor }"
  >
    <label>
      <input type="checkbox" v-model="isChecked" />
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow">删除</button>
  </li>
</template>
<script lang="ts">
import { Todo } from "../types/todo";
import { computed, defineComponent, ref, } from "vue";
export default defineComponent({
  name: "myItem",
  props: {
    todo: {
      type: Object as ()=> Todo,
      required: true,
    }
  },

  setup(props) {
    const isChecked = computed(()=> {
      return props.todo.isChecked
    });

    const isShow = ref("false");
    const bgColor = ref("white");
    const myColor = ref("black");
    const mousehandler = (flag: boolean) => {
      if (flag) {
        bgColor.value = "pink";
        myColor.value = "green";
      } else {
        bgColor.value = "white";
        myColor.value = "black";
      }
    };

    return {
      mousehandler,
      bgColor,
      myColor,
      isShow,
      isChecked,
    };
  },
});
</script>
<style>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  /* display: none; */
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>