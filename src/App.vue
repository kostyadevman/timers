<template>
  <div class="container">
    <timer-item 
      v-for="timer in timers" 
      :key="timer.id" 
      :timer="timer"
    />
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
import TimerItem from '@/components/TimerItem.vue'



export default defineComponent({
  components: {
    TimerItem
  },
  data() {
      return {
          timers: [{id: 1, seconds: 3}, {id: 2, seconds: 3600}]
      }
  },
  methods: {
    addTimer() {
      this.timers.push({
        id: this.timers.length + 1,
        seconds: Math.floor(Math.random() * 50000)
      })
    },
  }
})

</script>

<style scoped lang="scss">

.container {
  display: flex;
  flex-wrap: wrap;
  gap: 45px 50px;
  width: 775px;
  margin: 72px auto 72px;

  @media (max-width: 1025px) {
    width: 500px;
  }

  @media (max-width: 769px) {
    width: 225px;
  }
}
.add {
  width: 225px;
  height: 120px;
  border: none;
  background-color: var(--c-light-gray);
  &:hover {
      opacity: .7;
      cursor: pointer;
  }
}
</style>