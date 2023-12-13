<template>
  <section class="mission">
    <h2 class="mission__title">Миссия Softline</h2>
    <p class="mission__descr">
      Мы&nbsp;помогаем организациям трансформироваться, работать эффективно
      и&nbsp;безопасно в&nbsp;условиях цифровой экономики.
    </p>
  </section>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.mission {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
  height: 470px;
  padding: 0 72px;
  margin-bottom: 87px;
  color: #fff;
  background: $primary-color;
  position: relative;
  z-index: 0;

  &::before {
    position: absolute;
    left: 0;
    top: 0;
    content: "";
    background: url("../assets/images/left-pattern.svg") no-repeat left;
    height: 100%;
    width: 100%;
    z-index: -1;
  }

  &::after {
    position: absolute;
    right: 0;
    top: 0;
    content: "";
    background: url("../assets/images/right-pattern.svg") no-repeat right;
    height: 100%;
    width: 100%;
    z-index: -1;
  }

  &__title {
    @include P56-bold;
    color: $text-secondary;
    margin-bottom: 40px;
  }

  &__descr {
    @include P32;
    color: $text-secondary;
  }
}

@media screen and (max-width: $tableWidth) {
  .mission {
    margin: 20px 0 0;
    padding: 50px 5px;
    height: 290px;
  }
}
</style>
