<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";
import type { TodoItem } from "types";
import TodoList from "./components/TodoList.vue";
import { v4 as uuidv4 } from "uuid";

const text = ref("");
const todoList: Ref<TodoItem[]> = ref([]);

function addItem(): void {
  todoList.value.push({
    id: uuidv4(),
    text: text.value,
    isCompleted: false,
  });
  text.value = "";
}

function deleteItem(id: string): void {
  todoList.value = todoList.value.filter((item) => item.id !== id);
}
</script>

<template>
  <div class="flex justify-center items-center">
    <input type="text" v-model="text" />
    <button @click="addItem">Add Item</button>
    <TodoList :todo-list="todoList" @delete:item="deleteItem" />
  </div>
</template>



<style>
</style>
