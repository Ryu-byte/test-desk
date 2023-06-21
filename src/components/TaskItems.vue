<template>
  <div class="container">
    <div id="to-do-items">
      <p v-if="totalItems === 0">
        Sorry, you don't create any tasks :(
        Do you want to plan something?)
      </p>
      <TaskItem v-for="item in items" :key="item.id" :initialItem="item" />
    </div>
  </div>
</template>

<script>

import {useStore} from 'vuex';
import TaskItem from "@/components/TaskItem";
import {computed} from "vue";
export default {
  name: "TaskItems",
  components: {TaskItem},
  setup() {
    const store = useStore();
    const totalItems = computed(() => store.getters.totalItems);
    const items = computed(() => store.getters.items);
    return {
      totalItems,
      items
    }
  }
}
</script>

<style scoped>
#to-do-items {
  padding: 20px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
