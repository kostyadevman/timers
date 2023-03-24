<template>
  <div class="timer">
    <div class="timer__time" :class="{ active: this.active}">
        {{ renderTimer }}
    </div>
    <div class="timer__controls">
        <button v-if="active" class="timer__pause" :class="{ active: this.active}" @click="pauseTimer">
            <svg width="10" height="20" viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect x="7" width="3" height="20" fill="#9E9E9E"/>
                <rect width="3" height="20" fill="#9E9E9E"/>
            </svg>
        </button>
        <button v-if="!active" class="timer__start" @click="startTimer">
            <svg class="svg" width="17" height="20" viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 20V0L17 10L0 20Z" fill="#9E9E9E"/>
            </svg>
        </button>
        <button class="timer__stop" :class="{ active: this.active}" @click="stopTimer">
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="20" height="20" fill="#9E9E9E"/>
            </svg>
        </button>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    props: ["timer"],
    data() {
      return {
          seconds: this.$props.timer.seconds,
          intervalId: null,
          active: false
      }
    },
    computed: {
        renderTimer() {
            const h = Math.floor(this.seconds / 3600);
            const m = Math.floor(this.seconds / 60) % 60;
            const s = this.seconds % 60;
            return `${h}:${m}:${s}`
        }
    },
    methods: {
        startTimer() {
            this.active = true
            this.intervalId = setInterval(() => {
            if (this.seconds > 1) {
                this.seconds--;
            } else {
                this.stopTimer();
            }
            }, 1000)
        },
        stopTimer() {
            this.active = false;
            clearInterval(this.intervalId);
            this.seconds = 0;
        },
        pauseTimer() {
            this.active = false;
            clearInterval(this.intervalId);
        },
    }
})
</script>

<style scoped lang="scss">
.timer {
    width: 225px;
    height: 120px;
    background-color: var(--c-light-gray);

    &__time,
    &__controls {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 50%;
        border-bottom: 1px solid var(--c-soft-gray);
    }

    &__controls {
        border: none;
        gap: 50px;
    }

    &__start,
    &__pause,
    &__stop {
        width: 30px;
        border: none;
        background-color: transparent;
        cursor: pointer;

        &:hover {
            opacity: .7;
        }
    }

}

.timer .active {
    color: var(--c-white);
    svg rect {
        fill: var(--c-white);;
    }
    svg path {
        fill: var(--c-white);
    }
}
</style>