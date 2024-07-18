<template>
  <div class="blocknot w-[400px] h-[800px] bg-gray-400">
    <div
      class="bg-slate-300 h-10 w-full border border-red-600 mb-2 flex justify-between"
      v-for="(toDoItem, index) in toDoList"
      :key="index"
    >
      <input
        v-model="toDoItem.isDone"
        type="checkbox"
        name=""
        id=""
      />
      <span :class="{'line-through': toDoItem.isDone}">{{ toDoItem.description }}</span>
      <button @click="deleteItem(index)" class="right-1 bg-red-600 text-white">Удалить</button>
    </div>

    <input v-model="descriptionForNewItem" type="text" placeholder="Купить яйца">
    <button @click="addNewToDoItem" class="bg-slate-50 border ml-3">Добавить дело</button>
  </div>
</template>
<script setup>
import { ref } from "vue"

const toDoList = ref([
  { isDone: false, description: "Купить лимонов" },
  { isDone: true, description: "Сходить в магазин" },
  { isDone: false, description: "Сходить в магазин" },
  { isDone: true, description: "Сходить в магазин" },
])

const descriptionForNewItem = ref('')

const addNewToDoItem = () => {
  const newItem = { isDone: false, description: descriptionForNewItem.value }

  toDoList.value.push(newItem)

  descriptionForNewItem.value = ''
}

const deleteItem = (index) => {
  toDoList.value.splice(index, 1)
}


</script>
<style></style>
