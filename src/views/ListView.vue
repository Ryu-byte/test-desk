<template>
  <div class="list">
    <TaskInput />
    <TaskItems />
  </div>
</template>

<script setup>

import TaskItems from "@/components/TaskItems";
import TaskInput from "@/components/TaskInput";

</script>

<style scoped>
.list {
  max-width: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 40px auto;
}
</style>