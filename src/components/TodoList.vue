<script setup lang="ts">
import Item from "./Item.vue";
import type { TodoItem } from "types";
import type { PropType } from "vue";

const props = defineProps({
  todoList: {
    type: Object as PropType<TodoItem[]>,
    required: true,
  },
});

const emit = defineEmits<{
  (e: "delete:item", id: string): void;
}>();

function deleteItem(id: string): void {
    emit('delete:item', id)
}
</script>

<template>
  <div>
    <div v-for="todo in todoList" :key="todo.id">
      <Item :item="todo" @delete:item="deleteItem" />
    </div>
  </div>
</template>



<style lang="scss" scoped>
</style>