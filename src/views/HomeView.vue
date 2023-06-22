<template>
  <div class="home">
    <h1>Test Desk</h1>
    <div class="test-desk-header">
      <div class="container">
        <p v-if="totalItems">
          You have done {{ totalCompletedItems }} of {{ totalItems }} tasks
        </p>
        <div v-else>
          <p>You don't have any tasks in your list :( Any plans?</p>
          <VueUiButton text="Create task" class="create-button" @click=redirectToList />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

import {useStore} from "vuex";
import {computed} from "vue";
import {useRouter} from "vue-router/dist/vue-router";
import VueUiButton from "@/components/ui/VueUiButton";

const store = useStore();
const router = useRouter();
const redirectToList = () => {
  router.push('list')
}
const totalItems = computed(() => store.getters.totalItems);
const totalCompletedItems = computed(() => store.getters.totalCompletedItems);

</script>

<style scoped>
.test-desk-header {
  text-align: center;
  padding: 30px 0;
}

.test-desk-header h1 {
  font-size: 40px;
}

p {
  margin-bottom: 0;
}

.create-button {
  width: 200px;
  margin-top: 30px;
  padding: 10px;
  color: #555;
}
</style>