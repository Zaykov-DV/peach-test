<template>
<div class="tab">
  <span v-for="tab in names"
        :key="tab.name"
        :class="['tab__item', {'selected' : tab.name === selectedTab}]"
        @click="clickOnTab(tab.name)">
    {{tab.label}}
  </span>
</div>
</template>

<script setup>
const emit = defineEmits(['changeTab'])

const props = defineProps({
  names: {
    type: Array,
    required: true
  },
  selectedTab: {
    type: String
  }
})

const clickOnTab = (tabName) => {
  emit('changeTab', tabName)
}

</script>

<style lang="scss" scoped>
.tab {
  display: flex;

  &__item {
    display: block;
    height: 100%;
    margin-right: 30px;
    padding: 23px 0;
    border-bottom: 3px solid transparent;
    cursor: pointer;
    transition: all .3s ease-in-out;
    white-space: nowrap;

    &:last-child {
      margin-right: 0;
    }

    &.selected {
      color: $primary-color;
      border-bottom-color: $primary-color;
    }
  }
}

@media screen and (max-width: $smDesktopWidth) {
  .tab {
    &__item {
      padding: 0 0 20px 0;
      margin-right: 16px;
    }
  }
}
</style>
