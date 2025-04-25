<template>
  <div class="app-container">
    <h1 class="title">Мои задачи</h1>
    <ul class="task-list">
      <li v-for="task in tasks" :key="task.id" class="task-item">
        <label class="checkbox-container">
          <input type="checkbox" v-model="task.done" @change="saveTasks" />
          <span class="custom-checkbox"></span>
        </label>
        <span :class="{ done: task.done }" class="task-title">{{ task.title }}</span>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const tasks = ref([])

onMounted(async () => {
  const saved = localStorage.getItem('tasks')
  if (saved) {
    tasks.value = JSON.parse(saved)
  } else {
    const res = await fetch('/tasks.json')
    tasks.value = await res.json()
    saveTasks()
  }
})

function saveTasks() {
  localStorage.setItem('tasks', JSON.stringify(tasks.value))
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

.app-container {
  font-family: 'Inter', sans-serif;
  max-width: 480px;
  margin: 40px auto;
  padding: 24px;
  background: #f9f9f9;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.title {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 20px;
  color: #222;
}

.task-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.task-item {
  display: flex;
  align-items: center;
  padding: 12px 16px;
  background: #fff;
  border-radius: 12px;
  margin-bottom: 12px;
  transition: background 0.2s;
}

.task-item:hover {
  background: #f0f2f5;
}

.task-title {
  margin-left: 12px;
  font-size: 16px;
  color: #2c2c2c;
  transition: color 0.2s;
}

.task-title.done {
  color: #aaa;
  text-decoration: line-through;
}

.checkbox-container {
  position: relative;
  display: flex;
  align-items: center;
  cursor: pointer;
}

.checkbox-container input {
  opacity: 0;
  position: absolute;
}

.custom-checkbox {
  width: 20px;
  height: 20px;
  background-color: #e5e5e5;
  border-radius: 6px;
  transition: background-color 0.2s;
  display: inline-block;
  box-shadow: inset 0 0 0 2px #ccc;
}

.checkbox-container input:checked + .custom-checkbox {
  background-color: #4c75a3; /* vk-blue */
  box-shadow: inset 0 0 0 2px #4c75a3;
}
</style>
