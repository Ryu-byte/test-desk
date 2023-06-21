<template>
  <div class="list">
    <ToDoInput />
    <TaskItems />
  </div>
</template>

<script>

import {useStore} from "vuex";
import ToDoInput from "@/components/TaskInput";
import TaskItems from "@/components/TaskItems";

export default {
  components: {TaskItems, ToDoInput},
  setup() {
    const store = useStore();

    return {
      store,
    }
  },
}
</script>

<style scoped>

</style>