<script setup lang="ts">
import { ref } from 'vue';
import ListItem from './components/ListItem.vue'
import BeforeListItem from './components/BeforeListItem.vue'
const arr = ref([
  { id: 0, msg: 'hello world' },
  { id: 1, msg: 'message 2' },
  { id: 2, msg: 'learn vue!' },
  { id: 3, msg: 'next message!' },
  { id: 4, msg: 'yay!' },
])
const activeId = ref(0)
const beforeActiveId = ref(0)
</script>

<template>
  <div class="wrapper">
    <div>
      <button @click="activeId = (activeId + 1) % arr.length">Next</button>
      <ul>
        <list-item
          v-for="msg in arr"
          :key="msg.id"
          :id="msg.id"
          :msg="msg.msg"
          :is-active="msg.id === activeId"
        />
      </ul>
    </div>
    <div>
      <button @click="beforeActiveId = (beforeActiveId + 1) % arr.length">Next</button>
      <ul>
        <before-list-item
          v-for="msg in arr"
          :key="msg.id"
          :id="msg.id"
          :msg="msg.msg"
          :active-id="beforeActiveId"
        />
      </ul>
    </div>
  </div>
</template>

<style scoped>
#app {
  font-family: 'Avenir', Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px
}

.wrapper {
  display: flex;
  width: 500px;
  justify-content: space-between;
}
</style>
