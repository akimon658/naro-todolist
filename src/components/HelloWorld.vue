<script setup lang="ts">
import ClickCounter from './ClickCounter.vue'
import ItemList from './ItemList.vue'
import TaskList from './TaskList.vue'

defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <ClickCounter />
    <ItemList />
    <TaskList />
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
