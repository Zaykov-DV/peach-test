<template>
  <section class="banner">
    <div class="banner__content">
      <p class="banner__text">
        Поставщик услуг цифровой трансформации и&nbsp;кибербезопасности
      </p>
      <a class="banner__link" href="#" target="_blank">
        <Button label="На сайт" to="'htp'"/>
      </a>
    </div>
  </section>
</template>

<script setup>
import Button from "@/components/UI/Button.vue"

</script>


<style lang="scss">
.banner {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  height: 600px;
  padding: 0 70px;
  background-image: url("../assets/images/bg.jpg");
  background-repeat: no-repeat;

  &__text {
    @include P56-bold;
    max-width: 709px;
    color: $text-primary;
    margin-bottom: 60px;
  }

  &__link {
    border-bottom: none;
    &:hover {
      border-bottom: none;
    }
  }
}

@media screen and (max-width: $desktopWidth) {
  .banner {
    &__text {
      width: 80%;
      line-height: 100%;
    }
  }
}

@media screen and (max-width: $tableWidth) {
  .banner {
    padding: 15px;
    background-size: cover;
    height: 400px;

    &__text {
      width: 43%;
      margin-bottom: 20px;
    }
  }
}

@media screen and (max-width: $phoneWidth) {
  .banner {
    height: 300px;

    &__text {
      width: 67%;
    }
  }
}
</style>
