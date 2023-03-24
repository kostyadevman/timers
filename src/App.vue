<template>
  <div class="container">
    <timer v-for="timer in timers" :key="timer.id" :timer="timer"/>
    <button class="add" @click="addTimer">
      <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect x="8.5" width="3" height="20" fill="#9E9E9E"/>
        <rect y="11.5" width="3" height="20" transform="rotate(-90 0 11.5)" fill="#9E9E9E"/>
      </svg>
    </button>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import Timer from '@/components/Timer.vue'


export default defineComponent({
  components: {
    Timer,
  },
  data() {
      return {
          timers: [{id: 1, seconds: 300}, {id: 2, seconds: 3600}]
      }
  },
  methods: {
    addTimer() {
      this.timers.push(4)
    }
  }
})

</script>

<style scoped>

.container {
  display: flex;
  flex-wrap: wrap;
  gap: 50px;
  width: 775px;
}
.add {
  width: 225px;
  height: 120px;
}
</style>