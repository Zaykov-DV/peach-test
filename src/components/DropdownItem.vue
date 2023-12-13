<template>
  <div class="dropdown">
    <div class="dropdown__header" @click="openCities()">
      <p class="dropdown__title">{{ region.name }}</p>
      <IconDropdown class="dropdown__icon"
                    :class="{'is-open' : isCitiesShow}"
                    v-if="isMobile && region.cities.length"/>
    </div>
    <div v-if="isMobile">
      <transition name="fade">
        <div v-if="isCitiesShow">
          <p class="dropdown__text" v-for="city in region.cities">
            {{ city }}
          </p>
        </div>
      </transition>
    </div>
    <div v-else>
      <p class="dropdown__text" v-for="city in region.cities">
        {{ city }}
      </p>
    </div>
  </div>
</template>

<script setup>
import IconDropdown from "@/components/icons/IconDropdown.vue";
import {ref} from "vue";

defineProps({
  region: Array,
  isMobile: Boolean
})

const isCitiesShow = ref(false)

const openCities = () => {
  isCitiesShow.value = !isCitiesShow.value
}
</script>

<style scoped lang="scss">
.dropdown {

  &__header {
    display: flex;
    align-items: baseline;
  }

  &__icon {
    position: relative;
    bottom: 3px;
    margin-left: 3px;
    min-width: 8px;
    transition: rotate .3s ease-in-out;

    &.is-open {
      rotate: 180deg;
    }
  }

  &__title {
    @include P18-bold;
    margin-bottom: 10px;
  }

  &__text {
    @include P18;
    margin-bottom: 5px;
  }
}


@media screen and (max-width: $smDesktopWidth) {
  .dropdown {
    &__dropdown-title {
      margin-bottom: 0;
    }

    &__dropdown-text {
      margin-top: 5px;
    }
  }
}
</style>
