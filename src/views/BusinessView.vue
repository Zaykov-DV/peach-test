<template>
  <section class="business">
    <h2 class="business__title">Направления бизнеса</h2>
    <div class="business__cards">
      <Card v-for="(card, index) in cards"
            :key="index"
            :card="card"
            :isMobile="isMobile"
            :style="{ backgroundImage: `url('../assets/images/cards/${card.image}.jpg')` }"/>
    </div>
  </section>
</template>


<script setup>
import {ref} from 'vue'
import Card from "@/components/Card.vue";

const cards = ref([
  {
    title: 'Решения Softline',
    descr: 'ГК Softline предлагает клиентам собственную линейку оборудования (ПК, серверы, торговое оборудование и проч.), разработку программных продуктов, облачных решений, решений в области информационной безопасности.',
    image: 'card1'
  },
  {
    title: 'Кибербезопасность',
    descr: 'Softline обладает всеми необходимыми государственными лицензиями для организации проектов по информационной безопасности и аттестации. ',
    image: 'card2'
  },
  {
    title: 'Импортозамещение',
    descr: 'ГК Softline обладает широчайшим портфелем решений и услуг для импортозамещения, включая ПО и оборудование собственного производства.',
    image: 'card3'
  },
  {
    title: 'Облачные решения',
    descr: 'Softline использует современные облачные решения как российских, так и международных вендоров для масштабирования бизнеса своих клиентов. Подписки, услуги, трансформация.',
    image: 'card4'
  },
  {
    title: 'Цифровая трансформация\nи разработка ПО',
    descr: 'Softline использует современные технологи и новые возможности для увеличения производительности бизнеса заказчика. В штате ГК Softline - 2000+ разработчиков, которые трансформируют ПО под нужды конкретного предприятия.',
    image: 'card5'
  },
  {
    title: 'Техническая поддержка Softline',
    descr: '200+ инженеров, 24 часа в сутки, 7 дней в неделю, 12 месяцев в году, сервисное партнерство с 30+ мировыми производителями.',
    image: 'card6'
  }
])

defineProps({
  isMobile: Boolean
})

</script>

<style lang="scss">

.business {
  &__title {
    @include P56-bold;
    color: $text-primary;
    text-align: center;
    margin-bottom: 55px;
  }

  &__cards {
    display: grid;
    grid-template-columns: repeat(2, 50%);
    grid-template-rows: repeat(6, auto);
    column-gap: 9px;
    row-gap: 20px;
    margin-bottom: 100px;
  }

  &__card {
    position: relative;
    height: 260px;
    overflow: hidden;
    transition: height .3s ease-in-out;

    &:hover {
      .business__wrapper {
        height: 100%;
      }
    }
  }

  &__wrapper {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 80px;
    background: rgba($tertiary-color-rgb, .6);
    z-index: 1;
    transition: all 0.3s ease-out;
    color: #ffffff;
    padding: 0 20px;
  }

  &__card-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 28px 0;
    margin-bottom: 20px;
  }

  &__card-title {
    @include P24-bold;
  }

  &__card-text {
    @include P18;
  }

  &__card-arrow {
    transition: rotate .3s ease-in-out;

    &.is-open {
      rotate: 180deg;
    }
  }

}

@media screen and (max-width: 1249px) {
  .business {
    margin-top: 50px;

    &__cards {
      padding: 0 15px;
    }
  }
}

@media screen and (max-width: $tableWidth) {
  .business {

    &__card {
      height: 60px;

      &.is-open {
        height: 240px;

        .business__wrapper {
          height: 100%;
        }
      }
    }

    &__wrapper {
      top: 0;
      padding: 0 20px;

    }

    &__cards {
      grid-template-columns: 1fr;
    }

    &__card-header {
      padding: 10px 0;
      height: 60px;
      margin-bottom: 0;
    }

    &__card-text {
      line-height: 22px
    }
  }

}
</style>
