<template>
  <div class="to-do-item">
    <div class="item-left">
      <input type="checkbox" v-bind:checked="item.completed" v-on:change="changeCheck"/>
    </div>
    <input class="item" v-bind:class="{ completed: item.completed }" v-bind:disabled="!isEditing" v-model="item.title"
           v-on:keyup.enter="updateItem">
    <div class="item-right">
      <VueUiButton class="edit-button" @click="isEditing = true" text="Edit"/>
      <VueUiButton class="remove-button" @click="deleteItem(item.id)" text="Del"/>
    </div>
  </div>
</template>

<script setup>
import {useStore} from "vuex";
import {computed, ref} from "vue";
import VueUiButton from "@/components/ui/VueUiButton";

const props = defineProps({
  initialItem: {
    type: Object,
    required: true
  }
});
const emit = defineEmits(["updateItem"]);
const store = useStore();
const isEditing = ref(false)
const item = computed({
  get() {
    return props.initialItem;
  },
  set(value) {
    emit("updateItem", value);
  },
});
const updateItem = () => {
  store.commit('updateItem', {
    id: item.value.id,
    completed: item.value.completed,
    title: item.value.title
  });
  isEditing.value = false;
}
const deleteItem = (id) => {
  store.commit('deleteItem', {id});
}
const changeCheck = () => {
  item.value.completed = !item.value.completed;
  store.commit('updateItem', {
    id: item.value.id,
    completed: item.value.completed,
    title: item.value.title
  });
}
</script>

<style scoped>
.to-do-item {
  margin-bottom: 10px;
  position: relative;
  display: flex;
  width: 100%;
}

input.item {
  padding: 12px 15px 12px 35px;
  font-size: 20px;
  border-radius: 20px;
  border: 1px solid lightgray;
  color: black;
  outline: none;
  width: 100%;
}

input.completed {
  text-decoration: line-through;
  color: #007bff;
}

.item-right {
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 50%;
  right: 0%;
  transform: translate(-50%, -50%);
}


.item-left {
  position: absolute;
  top: 50%;
  left: 0%;
  transform: translate(50%, -50%);
}

.edit-button {
  background: #0093ff;
  color: wheat;
  margin-right: 5px;
}

.remove-button {
  background: red;
}

@media screen and (max-width: 600px) {
  .to-do-item {
    width: 100%;
  }
}
</style>
