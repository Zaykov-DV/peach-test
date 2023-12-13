<template>
  <button class="btn" @click="clickOnButton()">
    <span>{{ label }}</span>
  </button>
</template>

<script setup>
defineProps({
  label: {
    type: String,
    default: 'Button'
  }
})

const emit = defineEmits(['click'])

const clickOnButton = () => {
  emit('click')
}

</script>


<style lang="scss" scoped>

.btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 18px 28px;
  min-height: 56px;
  color: $btn-text-color;
  background-color: $btn-bg-color;
  border-radius: 8px;
  border: none;
  cursor: pointer;
  transition: background-color .3s ease-in-out;
  @include btn-text;

  &:hover {
    background-color: $btn-bg-color-hover;
  }
}

@media screen and (max-width: $tableWidth) {
  .btn {
    padding: 6px 25px;
    min-height: 32px;
  }
}
</style>
