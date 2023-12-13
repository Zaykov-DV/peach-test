<template>
  <Header />
  <BannerView />
  <AboutView :isMobile="isMobile"/>
  <LocationView :isMobile="isMobile"/>
  <MissionView />
  <BusinessView :isMobile="isMobile"/>
  <CompensationView />
  <CorporateLifeView :isMobile="isMobile" />
</template>
<script setup>
import Header from "@/components/Header.vue";
import BannerView from "@/views/BannerView.vue";
import AboutView from "@/views/AboutView.vue";
import LocationView from "@/views/LocationView.vue";
import MissionView from "@/views/MissionView.vue";
import BusinessView from "@/views/BusinessView.vue";
import CompensationView from "@/views/CompensationView.vue";
import CorporateLifeView from "@/views/CorporateLifeView.vue";

import {ref, watchEffect } from "vue";


const isMobile = ref(false)
const resizeHandler = () => {
  isMobile.value = window.innerWidth < 768;
}

watchEffect(() => {
  resizeHandler()
  window.addEventListener("resize", resizeHandler);
})
</script>
