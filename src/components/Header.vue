<template>
  <header class="header">
    <IconLogo />
    <nav>
      <ul class="header__links">
        <li class="header__link"><a href="#">Облачные решения</a></li>
        <li class="header__link"><a href="#">Кибербезопасность</a></li>
        <li class="header__link"><a href="#">Импортозамещение</a></li>
        <li class="header__link"><a href="#">Цифровая трансформация</a></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import IconLogo from "./icons/IconLogo.vue";
</script>

<style lang="scss" scoped>

.header {
  min-height: 85px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 70px;

  &__links {
    display: flex;
    align-items: center;
  }

  &__link {
    @include P18;
    color: $text-primary;
    padding-right: 20px;

    &:last-child {
      padding-right: 0
    }
  }
}

@media screen and (max-width: $smDesktopWidth) {
  .header {
    flex-direction: column;
    align-items: flex-start;
    padding: 15px;

    &__links {
      flex-wrap: wrap;
      gap: 20px;
      margin-top: 16px;
    }

    &__link {
      padding-right: 0;
    }
  }
}

@media screen and (max-width: $smPhoneWidth) {
  .header {
    &__links {
      gap: 5px 10px;
    }

    &__link {
      padding-right: 0;
    }
  }
}
</style>
