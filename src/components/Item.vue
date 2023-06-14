<script setup lang="ts">
import type { TodoItem } from "types";
import type { PropType } from "vue";

const props = defineProps({
  item: {
    type: Object as PropType<TodoItem>,
    required: true,
  },
});

const emit = defineEmits<{
  (e: 'delete:item', id: string): void
}>()
function deleteItem() :void {
    emit('delete:item', props.item.id)
}
</script>

<template>
  <div>
    <p>{{ item.text }}</p>
    <button>edit</button>
    <button @click="deleteItem">delete</button>
  </div>
</template>



<style lang="scss" scoped>
</style>