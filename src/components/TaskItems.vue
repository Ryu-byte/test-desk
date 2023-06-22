<template>
    <div class="to-do-items">
      <p v-if="totalItems === 0">
        The list of tasks is currently empty...
      </p>
      <TaskItem v-for="item in items" :key="item.id" :initialItem="item"/>
    </div>
</template>

<script setup>

import {useStore} from 'vuex';
import TaskItem from "@/components/TaskItem";
import {computed} from "vue";

const store = useStore();
const totalItems = computed(() => store.getters.totalItems);
const items = computed(() => store.getters.items);

</script>

<style scoped>
.to-do-items {
  padding: 20px 0;
  width: 100%;
}
</style>
