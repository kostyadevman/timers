<template>
  <div class="timer">
    <div class="timer__time">
        {{ timer.seconds }}
    </div>
    <div class="timer__controls">
        <button class="timer__start">
            <svg class="svg" width="17" height="20" viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 20V0L17 10L0 20Z" fill="#9E9E9E"/>
            </svg>
        </button>
        <button class="timer__pause">
            <svg width="10" height="20" viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect x="7" width="3" height="20" fill="#9E9E9E"/>
                <rect width="3" height="20" fill="#9E9E9E"/>
            </svg>
        </button>
        <button class="timer__stop">
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
            timers: [1, 2, 3]
        }
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
    }

    &__start,
    &__pause,
    &__stop {
        border: none;
        background-color: transparent;
        cursor: pointer;

        &:hover {
            opacity: .7;
        }
    }

}
</style>