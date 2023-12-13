<template>
  <div class="business__card" :class="{'is-open' : isDescrOpen}" @click="openDescr()">
    <div class="business__wrapper">
      <div class="business__card-header">
        <h3 class="business__card-title">{{ card.title }}</h3>
        <IconArrowDown class="business__card-arrow" v-if="isMobile" :class="{'is-open' : isDescrOpen}"/>
      </div>
      <p class="business__card-text">{{ card.descr }}</p>
    </div>
  </div>
</template>

<script setup>
import IconArrowDown from "@/components/icons/IconArrowDown.vue";
import {ref} from "vue";

defineProps({
  isMobile: Boolean,
  isDescrOpen: Boolean,
  card: Object
})

const isDescrOpen = ref(false)

const openDescr = () => {
  isDescrOpen.value = !isDescrOpen.value
}
</script>
