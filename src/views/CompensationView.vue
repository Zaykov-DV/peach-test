<template>
  <section class="compensation">
    <div class="compensation__block">
      <div class="compensation__header">
        <h2 class="compensation__title">Компенсационный пакет</h2>
      </div>
      <div class="compensation__row">
        <div class="compensation__item" v-for="(item, index) in compensations" :key="index">
          <div class="compensation__icon"
               :style="{ backgroundImage: `url('../src/assets/images/icons/${item.icon}.svg')` }"></div>
          <span class="compensation__text">{{ item.title }}</span>
        </div>
      </div>
    </div>
    <div class="compensation__block">
      <div class="compensation__header">
        <h3 class="compensation__subtitle">
          Программа дополнительной мотивации
        </h3>
        <h3 class="compensation__subtitle compensation__subtitle_accent">доплата 12% от суммы</h3>
      </div>
      <div class="compensation__row">
        <div class="compensation__item" v-for="(item, index) in motivation" :key="index">
          <div class="compensation__icon"
               :style="{ backgroundImage: `url('../src/assets/images/icons/${item.icon}.svg')` }"></div>
          <span class="compensation__text">{{ item.title }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {ref} from 'vue'

const compensations = ref([
  {
    title: 'Дмс',
    icon: 'dms'
  },
  {
    title: 'Выходной \nв день рождения',
    icon: 'birthday'
  },
  {
    title: 'Корпоративная мобильная связь',
    icon: 'mobile'
  },
  {
    title: 'Корпоративные скидки \n на спорт',
    icon: 'sport'
  },
  {
    title: 'LTI',
    icon: 'lti'
  },
])

const motivation = ref([
  {
    title: 'Оргтехники',
    icon: 'print'
  },
  {
    title: 'ДМС',
    icon: 'dms'
  },
  {
    title: 'Ипотеки',
    icon: 'mortgage'
  }
])
</script>

<style lang="scss" scoped>
.compensation {
  width: 88%;
  margin: 0 auto 100px;
  padding: 62px 76px;
  box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.08);
  box-sizing: border-box;

  &__block {
    display: flex;
    flex-direction: column;

    &:first-child {
      padding-bottom: 75px;
      margin-bottom: 70px;
      border-bottom: 1px solid rgba(0, 0, 0, 0.1);
    }
  }

  &__header {
    margin-bottom: 50px;
  }

  &__title {
    @include P56-bold;
    color: $text-primary;
    text-align: center;
  }

  &__subtitle {
    @include P40-bold;
    color: $text-primary;
    text-align: center;

    &_accent {
      color: $text-accent;
    }
  }

  &__text {
    @include P18;
    color: $text-primary;
    text-align: center;
    text-transform: uppercase;
  }

  &__row {
    display: flex;
    justify-content: center;
    gap: 16px;
  }

  &__item {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 178px;
  }

  &__icon {
    width: 110px;
    height: 110px;
    margin-bottom: 10px;
    background-color: rgba(0, 0, 0, 0.05);
    background-repeat: no-repeat;
    background-position: center;
    background-size: 48px 48px;
    border-radius: 50px;
  }
}

@media screen and (max-width: $tableWidth) {
  .compensation {
    width: 100%;
    padding: 24px 5px;
    margin: 0 auto 50px;

    &__row {
      gap: 10px;
      flex-wrap: wrap;
    }

    &__item {
      width: 120px;
    }

    &__icon {
      width: 80px;
      height: 80px;
      background-size: 35px 35px;
    }

    &__block {
      &:first-child {
        padding-bottom: 24px;
        margin-bottom: 24px;
      }
    }
  }
}
</style>
