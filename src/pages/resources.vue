<template>
  <div class="page">
    <p class="big-header header-font"
      data-aos="zoom-in"
      data-aos-duration="1200"
    >
      Browse Our Resources
    </p>
    <p class="main-text text-block"
      data-aos="fade-up"
      data-aos-duration="1200"
      data-aos-delay="100"
    >{{ resourceIntro }}</p>

    <div style="margin-top: 40px;"></div>

    <p class="page-header header-font"
      data-aos="fade-up"
      data-aos-duration="1200"
    >
      Suggested Books
    </p>
    <BookList />
  </div>
</template>

<script lang="ts" setup>
import { onMounted, ref } from 'vue';
import AOS from 'aos'
import 'aos/dist/aos.css'

onMounted(() => {
  AOS.init()
  windowWidth.value = window.innerWidth
  window.addEventListener('resize', () => {
    windowWidth.value = window.innerWidth
  })
})

let windowWidth = ref(0)

const resourceIntro = ref('We live in a world of mind-numbing technology and entertainment. Surrounding ourselves with positive and enlightening content helps us accomplish the mission of The Arena to improve our lives in meaningful ways. Please explore the books, podcasts, and other resources we have to offer!')

</script>

<style scoped>
@import '@/styles/style.css';

</style>