<template>
  <main class="about">
    <div class="about__info">
      <p class="about__text"><b class="about__text about__text_accent">Softline</b> – ведущий поставщик IT-решений
        и сервисов.*
        Мы предлагаем комплексные IT-решения, облака, программное
        и аппаратное обеспечение, решения по цифровой трансформации
        и кибербезопасности, а также широкий спектр IT-услуг.</p>
    </div>
    <div class="about__numbers" v-if="!isMobile">
      <div class="about__numbers-wrapper">
        <div class="about__item">
          <span class="about__number">
            > <Counter :max=30 :start=20 /> лет</span>
          <span class="about__descr">на IT-рынке</span>
        </div>
        <div class="about__item">
          <span class="about__number"><Counter :max=4600 :start="4480"/></span>
          <span class="about__descr">сотрудников в России</span>
        </div>
        <div class="about__item">
          <span class="about__number"><Counter :max=25 :start="18"/></span
          ><span class="about__descr">городов России</span>
        </div>
      </div>
      <div class="about__numbers-wrapper">
        <div class="about__item">
          <span class="about__number"><Counter :max=2000 :start="1875"/> +</span
          ><span class="about__descr">разработчиков</span>
        </div>
        <div class="about__item">
          <span class="about__number"><Counter :max=3000 :start="2875"/> +</span>
          <span class="about__descr">
            сотрудников ежегодно <br> проходят оценку и обучение
          </span>
        </div>
      </div>
    </div>
    <div class="about__numbers" v-if="isMobile">
      <div class="about__numbers-wrapper">
        <div class="about__item">
          <span class="about__number">> <Counter :max=30 :start=20 /> лет</span>
          <span class="about__descr">на IT-рынке</span>
        </div>
        <div class="about__item">
          <span class="about__number"><Counter :max=4600 :start="4480"/></span>
          <span class="about__descr">сотрудников в России</span>
        </div>
      </div>
      <div class="about__numbers-wrapper">
        <div class="about__item">
          <span class="about__number"><Counter :max=25 :start="18"/></span
          ><span class="about__descr">городов России</span>
        </div>
        <div class="about__item">
          <span class="about__number"><Counter :max=2000 :start="1875"/> +</span
          ><span class="about__descr">разработчиков</span>
        </div>
      </div>
      <div class="about__numbers-wrapper">
        <div class="about__item about__item_last">
          <span class="about__number"><Counter :max=3000 :start="2875"/> +</span>
          <span class="about__descr">
            сотрудников ежегодно <br> проходят оценку и обучение
          </span>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import Counter from "@/components/Counter.vue";

defineProps({
  isMobile: Boolean
})

</script>

<style lang="scss" scoped>
.about {
  width: 100%;
  margin: 97px auto;

  &__text {
    @include P32-bold;
    color: $text-primary;

    &_accent {
      color: $text-accent;
    }
  }

  &__info {
    width: 88%;
    margin: 0 auto 100px;
    padding: 100px 110px;
    box-shadow: 0 0 32px 0 rgba(0, 0, 0, 0.08);
    line-height: 120%;
    text-align: center;
  }

  &__numbers-wrapper {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin: 0 180px;

    &:first-child {
      margin-bottom: 80px;
    }

    &:last-child {
      padding: 0 120px;
    }
  }

  &__item {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  &__number {
    @include P80-bold;
    color: $text-accent;
    white-space: nowrap;
  }

  &__descr {
    @include P18;
    color: $text-primary;
  }
}

@media screen and (max-width: 1068px) {
  .about__numbers-wrapper:last-child {
    padding: 0 60px;
  }
}


@media screen and (max-width: $smDesktopWidth) {
  .about__numbers-wrapper {
    margin: 0 90px 40px;
  }
}

@media screen and (max-width: $tableWidth) {
  .about {
    margin-top: 60px;

    &__info {
      width: auto;
      margin: 0 15px 50px;
      padding: 24px 5px;
    }

    &__numbers-wrapper {
      margin: 0 15px;
      justify-content: space-evenly;

      &:first-child {
        margin-bottom: 24px;
      }

      &:last-child {
        margin-top: 24px;
      }
    }

    &__item {
      align-items: center;
      text-align: center;
      margin-right: 8px;

      &_last {
        min-width: 180px;
      }
    }
  }
}
</style>
