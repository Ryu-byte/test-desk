<template>
  <div class="home">
    <h1>This is a home page</h1>
    <div id="to-do-header">
      <div class="container">
        <h1>Welcome to VueDo</h1>
        <p>Completed {{ totalCompletedItems }} of {{ totalItems }} tasks</p>
      </div>
    </div>
  </div>
</template>

<script>

import {useStore} from "vuex";
import {computed} from "vue";

export default {
  name: "HomeView",
  setup() {
    const store = useStore();
    const totalItems = computed(() => store.getters.totalItems);
    const totalCompletedItems = computed(() => store.getters.totalCompletedItems);

    return {
      store,
      totalItems,
      totalCompletedItems
    }
  },
}
</script>

<style scoped>
#to-do-header {
  background: #80bdab;
  text-align: center;
  padding: 30px 0;
  color: white;
}

#to-do-header h1 {
  font-size: 40px;
}

p {
  margin-bottom: 0;
}
</style>