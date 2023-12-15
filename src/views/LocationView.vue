<template>
  <section class="location">
    <div class="location__tab-menu">
      <div class="location__wrapper">
        <p class="location__text">Офисы Softline</p>
        <IconArrow class="location__icon"
                   @click="toggleMenu()"
                   :class="{'is-open': isDropdownOpen}"/>
      </div>
      <transition name="fade">
        <div class="location__dropdown" v-if="isDropdownOpen">
          <div class="location__dropdown-block" v-for="region in regions">
            <DropdownItem :region="region"
                          :isMobile="isMobile"/>
          </div>
        </div>
      </transition>
      <Tabs class="location__tabs"
            :class="{'is-open': isDropdownOpen}"
            :names="tabs"
            :selectedTab="selectedTab"
            @changeTab="changeTab">
      </Tabs>
    </div>
    <div class="location__map" :class="{'is-open': isDropdownOpen}">
      <img class="location__image" src="@/assets/images/map.jpg" :alt="'map'">
      <CitiesLocation class="location__svg" :checkedCity="selectedTab"/>
    </div>
  </section>
</template>

<script setup>
import {ref} from 'vue'

import Tabs from '@/components/UI/Tabs.vue'
import IconArrow from "@/components/icons/IconArrow.vue";
import DropdownItem from "@/components/DropdownItem.vue";
import CitiesLocation from "@/components/CitiesLocation.vue";

defineProps({
  isMobile: Boolean
})


const tabs = ref([
  {name: 'all', label: 'Все'},
  {name: 'moscow', label: 'Москва'},
  {name: 'center', label: 'Центр'},
  {name: 'north-west', label: 'Северо-Запад'},
  {name: 'south', label: 'Юг'},
  {name: 'volga', label: 'Волга'},
  {name: 'ural', label: 'Урал'},
  {name: 'siberia', label: 'Сибирь'},
  {name: 'east', label: 'Дальний Восток'}
])

const regions = ref([
  {name: 'Москва', cities: []},
  {name: 'Центр', cities: ['Воронеж', 'Ярославль', 'Белгород']},
  {name: 'Северо-Запад', cities: ['Санкт-Петербург', 'Калининград']},
  {name: 'Юг', cities: ['Ростов-на-Дону', 'Краснодар', 'Волгоград']},
  {name: 'Волга', cities: ['Казань', 'Самара', 'Уфа', 'Оренбург', 'Нижний Новгород']},
  {name: 'Урал', cities: ['Екатеринбург', 'Челябинск', 'Пермь', 'Сургут', 'Тюмень', 'Ижевск']},
  {name: 'Сибирь', cities: ['Новосибирск', 'Омск', 'Томск', 'Красноярск', 'Иркутск']},
  {name: 'Дальний Восток', cities: ['Хабаровск', 'Владивосток']},
])

const changeTab = (tabName) => {
  selectedTab.value = tabName
}

const selectedTab = ref('all')

const isDropdownOpen = ref(false)

const toggleMenu = () => {
  isDropdownOpen.value = !isDropdownOpen.value
}

</script>

<style scoped lang="scss">
.location {

  &__tab-menu {
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    background: #FFF;
    box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.06);
    padding: 0 70px;
    margin-bottom: 80px;
  }

  &__wrapper {
    display: flex;
    align-items: center;
  }

  &__icon {
    margin-left: 16px;
    transition: rotate .3s ease-in-out;

    &.is-open {
      rotate: 180deg;
    }
  }

  &__text {
    @include P24-bold;
    color: $text-primary;
  }

  &__map {
    position: relative;
    max-width: 1250px;
    width: 100%;
    height: 600px;
    //background: url("../assets/images/map.jpg") no-repeat left;
    transition: opacity .3s ease-in-out;
    overflow-x: scroll;
    overflow-y: hidden;

    &.is-open {
      opacity: .1;
    }
  }

  &__image {
    width: 100%;
    min-width: 1190px;
    min-height: 600px;
    height: auto;
  }

  &__svg {
    position: absolute;
    top: 122px;
    left: 6px;
  }

  &__tabs {
    transition: opacity .3s ease-in-out;

    &.is-open {
      opacity: .1;
    }
  }

  &__dropdown {
    position: absolute;
    z-index: 1;
    top: 95px;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: space-between;
    padding: 30px 68px;
    background-color: #fff;
  }

  &__dropdown-block {
    margin-right: 24px;

    &:last-child {
      margin-right: 0;
    }
  }
}

@media screen and (max-width: 1024px) {
  .location {
    &__text {
      font-size: 20px;
    }
  }
}

@media screen and (max-width: $smDesktopWidth) {
  .location {

    &__tabs {
      margin-top: 20px;
    }

    &__tab-menu {
      flex-direction: column;
      align-items: flex-start;
      padding: 20px 70px;
    }

    &__map {
      height: 400px;
    }

    &__image {
      width: 100%;
      min-width: 792px;
      min-height: 400px;
      height: 100%;
    }

    &__svg {
      width: auto;
      height: 83%;
      top: 80px;
      left: 4px;
    }

    &__dropdown {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 15px;
      top: 50px;
    }
  }
}

@media screen and (max-width: $tableWidth) {
  .location {
    &__dropdown {
      gap: 10px;
      padding: 20px 70px;
    }

    &__dropdown-block {
      margin: 0;
    }
  }
}


@media screen and (max-width: $phoneWidth) {
  .location {
    &__tabs {
      width: 100%;
      overflow-x: scroll;
    }

    &__tab-menu {
      padding: 18px 25px;
    }

    &__dropdown {
      padding: 18px 25px;
    }
  }
}
</style>
