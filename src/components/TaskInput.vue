<template>
  <div class="to-do-input">
    <input type="text" placeholder="Add what you want to plan" id="input" class="add-item" v-model="title" v-on:keyup.enter="addItem">
    <VueUiButton v-on:click="addItem" text="Add" class="add-button"/>
  </div>
</template>

<script setup>
import {useStore} from "vuex";
import {ref} from "vue";
import { uuid } from 'vue-uuid';
import VueUiButton from "@/components/ui/VueUiButton";

const store = useStore();
const title = ref("");
const addItem = () => {
  if (title.value.trim() === '') {
    return;
  }
  store.commit('addItem', {
    title: title.value,
    completed: false,
    id: uuid.v4()
  });
  title.value = '';
}

</script>

<style scoped>

.to-do-input {
  height: 40px;
  display: flex;
  width: 100%;
}

.add-item {
  height: 38px;
  margin-right: 5px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  outline: none;
  width: 100%;
}

.add-button {
  background: #00ff9794;
  color:floralwhite;
  padding: 0 10px;
}

@media screen and (max-width: 600px) {
  .to-do-input {
    flex-direction: column;
    height: 80px;
  }

  input {
    width: 100%;
  }

}
</style>
