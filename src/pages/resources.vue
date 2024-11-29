<template>
  <div class="page">
    <p class="big-header header-font"
      style="color: #2F5D3F;"
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
  
    <!-- <div style="margin-top: 40px;"></div>
    <hr style="height: 2px; width: 90%;" />
    <div style="margin-top: 40px;"></div> -->

    <!-- <div class="resource-wrapper">
      <div class="resource-col">
        <p class="page-header header-font"
          data-aos="fade-up"
          data-aos-duration="1200"
        >
          Podcasts
        </p>
        <ResourceList :resources="podcasts" />
      </div>

      <div class="resource-col">
        <p class="page-header header-font"
          data-aos="fade-up"
          data-aos-duration="1200"
        >
          Other Resources
        </p>
        <ResourceList :resources="otherResources" />
      </div>
    </div> -->

    <div style="margin-top: 40px;"></div>

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

const resourceIntro = ref('We live in a world of mind-numbing technology and entertainment. Surrounding ourselves with positive and enlightening content helps us accomplish the mission of The Arena to improve our lives in meaningful ways. Please explore the various books we have suggested!')
const podcasts = ref([
  {
    title: "Man Enough",
    author: "Justin Baldoni, Liz Plank, and Jamey Heath",
    url: "https://manenough.com/podcast/",
    blurb: "Explores what it means to be a man, and human, in the world today?",
    image: "resources/man-enough.png"
  },
]);

const otherResources = ref([
  {
    title: "\"I Love You, Bro\" project",
    author: "Joe Tuia\'ana, Founder",
    url: "https://www.iloveyoubroproject.org/",
    blurb: "A nonprofit dedicated to men\'s mental health, suicide prevention, and ongoing personal development.",
    image: "resources/love-you-bro.png"
  },
]);
</script>

<style scoped>
@import '@/styles/style.css';

@media (max-width: 850px) {
  .resource-wrapper {
    flex-direction: column;
  }
}

@media (min-width: 851px) {
  .resource-wrapper {
    flex-direction: row;
  }
}

.resource-wrapper {
  flex: 1;
  display: flex;
  align-items: start;
  gap: 20px;
}

.resource-col {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

</style>