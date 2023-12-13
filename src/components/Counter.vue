<template>
  <span class="counter" ref="counter">
    {{ counterValue }}
  </span>
</template>

<script setup>
import {ref, onMounted, onBeforeUnmount} from 'vue'

const props = defineProps({
  max: Number,
  start: Number
})


const counterValue = ref(0)
const counter = ref(null)

const onScroll = () => {
  if (counter.value.offsetTop + counter.value.offsetHeight < window.scrollY + window.innerHeight) {
    removeScrollHandler();
    const interval = setInterval(() => {
      if (++counterValue.value === props.max) {
        clearInterval(interval);
      }
    }, 2000 / props.max);
  }
}

const removeScrollHandler = () => {
  window.removeEventListener('scroll', onScroll);
}

onMounted(() => {
  window.addEventListener('scroll', onScroll);
  counterValue.value = props.start
  onScroll();
})

onBeforeUnmount(() => {
  removeScrollHandler()
})

</script>

<style scoped lang="scss">
  .counter {
    font-size: inherit;
    font-weight: inherit;
  }
</style>
