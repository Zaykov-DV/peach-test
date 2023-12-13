<template>
  <section class="life">
    <div class="life__header">
      <h3 class="life__title">Корпоративная жизнь</h3>
      <div class="life__navigation" v-if="!isMobile">
        <IconSliderNext ref="next" class="life__navigation-btn next"/>
        <IconSliderPrev ref="prev" class="next"/>
      </div>
    </div>
    <swiper :navigation="{ prevEl: '.prev', nextEl: '.next' }" :modules="modules" :loop="true" :pagination="pagination">
      <swiper-slide v-for="slide in slides">
        <img class="life__image" :src="getImageUrl(slide.image)" :alt="`${slide.image}`">
      </swiper-slide>
    </swiper>
    <div class="life__pagination"></div>
  </section>
</template>


<script setup>
import {ref} from 'vue'
import {Swiper, SwiperSlide} from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/navigation';
import {Navigation, Pagination} from 'swiper/modules';
import IconSliderNext from "@/components/icons/IconSliderNext.vue";
import IconSliderPrev from "@/components/icons/IconSliderPrev.vue";

const modules = [Navigation, Pagination]

const getImageUrl = (name) => {
  return new URL(`../assets/images/slides/${name}.jpg`, import.meta.url).href
}

const pagination = ref(
    {
      el: '.life__pagination',
      clickable: true,
      renderBullet: function (index, className) {
        return '<span class="' + className + '"></span>';
      }
    }
)

defineProps({
  isMobile: Boolean
})

const slides = ref([
  {
    image: 'slide1'
  },
  {
    image: 'slide2'
  },
  {
    image: 'slide3'
  },
  {
    image: 'slide4'
  },
  {
    image: 'slide5'
  }
])
</script>

<style lang="scss">
.life {
  padding: 0 70px 140px;

  &__header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 58px;
  }

  &__title {
    @include P56-bold;
    color: $text-primary;
  }

  &__image {
    max-height: 834px;
  }

  &__navigation-btn {
    margin-right: 10px;
  }

  &__pagination {
    display: flex;
    margin-top: 28px;
  }
}

@media screen and (max-width: $tableWidth) {
  .life {
    padding: 0 20px 50px;
    &__header {
      margin-bottom: 15px;
    }
  }
}

.swiper-pagination-bullet {
  display: block;
  height: 6px;
  width: 100%;
  transition: background-color .3s ease-in-out;
  background-color: rgba(0, 0, 0, 0.1);
  margin-right: 10px;

  &:last-child {
    margin-right: 0;
  }
}

.swiper-pagination-bullet-active {
  background-color: #A30C33;
}
</style>
