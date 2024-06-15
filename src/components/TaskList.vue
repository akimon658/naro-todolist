<script setup lang="ts">
import { computed,ref } from 'vue'

interface Task {
  name: string
  done: boolean
}

const tasks=ref<Task[]>([])
const newTaskName=ref<string>('')

const addTask=() => {
  if(newTaskName.value) {
    tasks.value.push({
      name: newTaskName.value,
      done: false,
    })
    newTaskName.value=''
  }
}

const markAsDone=(task: Task) => {
  task.done=true
}
</script>

<template>
  <div>
    <div>To Do リスト</div>
    <label>
      新しいタスク
      <input
        v-model="newTaskName"
        type="text"
      />
    </label>
    <button @click="addTask">作成</button>
    <div>やること</div>
    <ul>
      <div
        v-for="task in tasks"
        :key="task.name"
      >
        <li v-if="!task.done">
          {{ task.name }}
          <button @click="markAsDone(task)">Done!</button>
        </li>
      </div>
    </ul>
    <div>完了</div>
    <ul>
      <div
        v-for="task in tasks"
        :key="task.name"
      >
        <li v-if="task.done">
          {{ task.name }}
        </li>
      </div>
    </ul>
  </div>
</template>
