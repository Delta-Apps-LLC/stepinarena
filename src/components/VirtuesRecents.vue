<template>
    <div class="component">
        <div class="virtues-recents-wrapper">
            <div class="virtues-section">
                <p class="page-header header-font"
                    data-aos="fade-up"
                    data-aos-duration="1200"
                >Core Virtues</p>
                <sl-carousel class="vertical"
                    v-if="windowWidth < 1000"
                    pagination
                    :slides-per-page="windowWidth < 650 ? '2' : windowWidth <= 1000 ? '3' : '4'"
                    slides-per-move="1"
                    orientation="vertical"
                >
                    <sl-carousel-item
                        v-for="(virtue, i) in virtues"
                        :key="i"
                    >
                        <div class="virtue-wrapper">
                            <div class="virtue-row">
                                <div class="circle"
                                    data-aos="fade-right"
                                    data-aos-duration="1200"
                                >
                                    <p class="header-font" id="virtue-title">{{ virtue.title }}</p>
                                    <v-icon id="virtue-icon"
                                        :size="windowWidth < 750 ? '30' : windowWidth <= 1300  ? '35' : windowWidth <= 1700 ? '40' : '45'"
                                    >{{ virtue.icon }}</v-icon>
                                </div>
                                <p class="virtue-details"
                                    data-aos="fade-left"
                                    data-aos-duration="1200"
                                >{{ virtue.details }}</p>
                            </div>
                        </div>
                    </sl-carousel-item>
                </sl-carousel>

                <div class="virtue-wrapper"
                    v-if="windowWidth > 1000"
                    style="width: 90%;"
                >
                    <div class="virtue-row"
                        v-for="(virtue, i) in virtues"
                        :key="i"
                    >
                        <div class="circle"
                            data-aos="fade-right"
                            data-aos-duration="1200"
                        >
                            <p class="header-font" id="virtue-title">{{ virtue.title }}</p>
                            <v-icon id="virtue-icon"
                            :size="windowWidth <= 1300  ? '35' : windowWidth <= 1700 ? '40' : '45'"
                            >{{ virtue.icon }}</v-icon>
                        </div>
                        <p class="virtue-details"
                            data-aos="fade-left"
                            data-aos-duration="1200"
                        >{{ virtue.details }}</p>
                    </div>
                </div>
            </div>

            <div class="recents-section">
                <div class="featured-item-wrapper"
                    data-aos="fade-up-right"
                    data-aos-duration="1200"
                >
                    <p class="page-header header-font">Recent Challenge</p>
                    <div class="featured-item">
                        <p class="featured-item-title item-title">{{ featuredChallenge.title }}</p>
                        <p class="featured-item-description main-text">{{ featuredChallenge.description }}</p>
                        <p class="main-text" style="font-size: 14px; margin-bottom: 5px;">{{ featuredChallenge.date }}</p>
                    </div>
                    <RouterLink class="router-link" style="margin-top: 5px;" to="/events">View All</RouterLink>
                </div>

                <div class="featured-item-wrapper"
                    data-aos="fade-up-left"
                    data-aos-duration="1200"
                >
                    <p class="page-header header-font">Recent Event</p>
                    <div class="featured-item">
                        <p class="featured-item-title item-title">{{ featuredEvent.title }}</p>
                        <div class="featured-item-description main-text">
                            <img class="event-img" src="../assets/images/dog-lake/DSC00537.jpg" />
                        </div>
                        <p class="main-text" style="font-size: 14px; margin-bottom: 5px;">{{ featuredChallenge.date }}</p>
                    </div>
                    <RouterLink class="router-link" style="margin-top: 5px;" to="/events">View All</RouterLink>
                </div>
                
                <div class="featured-item-wrapper"
                    data-aos="fade-up"
                    data-aos-duration="1200"
                >
                    <p class="page-header header-font">Recent Blog</p>
                    <div class="featured-item">
                        <p class="featured-item-title item-title">{{ featuredBlog.title }}</p>
                        <p class="featured-item-description main-text">{{ featuredBlog.description }}</p>
                        <p class="main-text" style="font-size: 14px; margin-bottom: 5px;">{{ featuredChallenge.date }}</p>
                    </div>
                    <div style="display: flex; flex-direction: row; justify-content: center; margin-top: 5px;">
                        <RouterLink class="router-link" to="/blog">Read Blog</RouterLink>
                        <RouterLink class="router-link" to="/blog">View All</RouterLink>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue'
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

const virtues = ref([
  {
    title: 'Action',
    details: 'Take it. As men in The Arena we prioritize the real and concrete over the abstract. While others are talking we are doing. We are active participants in our lives, our relationships, and our community. We understand that motivation follows action and therefore we do not wait to feel motivated. Instead we act. And if we fail in our actions? At least we fail "while daring greatly."',
    icon: 'mdi-run-fast'
  },
  {
    title: 'Strength',
    details: 'Physical strength is a cornerstone of being a man. We value, prioritize and develop strength. We do so to be better protectors of those in our care and to be useful to those around us who may need our strength. We do so because we understand that physicality and being active means we can enjoy a longer, healthier, happier existence. We do so because strength is never a disadvantage.',
    icon: 'mdi-weight-lifter'
  },
  {
    title: 'Honor',
    details: 'We are concerned about our reputation among our fellow men in the arena and we do nothing which will jeopardize that reputation. We understand there are expectations to be met by us as individuals and as members of the group and we understand that the greatness of honor can not only be gained, it can more importantly, be lost. We strive to do everything in our power to not lose our honor.',
    icon: 'mdi-medal'
  },
  {
    title: 'Boldness',
    details: 'Inextricably linked to action, boldness is required when our inner critic is raging, telling us we should give into timidity. It is a willingness to confidently take calculated risks even though the outcome is uncertain. When everything is telling us to stay within the comfort of our little circle, boldness is our truest self encouraging us to enthusiastically step outside and embrace the growth of discomfort. We boldly go and do.',
    icon: 'mdi-fire'
    // icon: 'mdi-exclamation-thick'
  },
  {
    title: 'Fortitude',
    details: 'Suffering is required at times, but misery is optional. It is the virtue of fortitude which gives us durability in the toughest of circumstances and allows us to bear our misfortunes well. With it we resist the urge to crumble under the immense weight of seemingly unbearable trials. With it, we are a rock for others.',
    icon: 'mdi-chess-rook'
  },
  {
    title: 'Resolution',
    details: 'The world is full of good intentions. It is full of unfulfilled dreams. It is full of endless New Year’s resolutions which at the end of January are merely cold remnants of a once burning fire. We set ourselves apart as men through an unshakable resolution to do what we should and nothing can deter us in that resolution.',
    icon: 'mdi-compass-rose'
  },
])

const featuredChallenge = ref({
  title: 'New Skill/Read 30 Minutes',
  description: 'Spend time learning a new hard skill, and spend at least 30 minutes per day reading content that improves your mind or your life in a meaningful way.',
  date: '2024-11-16'
})

const featuredBlog = ref({
  title: 'Some sort of blog title',
  description: 'This is a preview text of the blog that will be featured. There will be a cutoff of a certain number of characters, and then they can click to read the whole blog.',
  date: '2024-10-5'
})

const featuredEvent = ref({
  title: 'Dog Lake Hike',
  image: "../assets/images/dog-lake/DSC00537.jpg",
  // description: 'The men got together and hiked up to Dog Lake in Big Cottonwood Canyon.',
  date: '2024-10-12'
})

</script>

<style scoped>
@import '@/styles/style.css';
@import '@/styles/virtues.css';

@media (max-width: 1000px) {
    .virtues-recents-wrapper {
        width: 90%;
        margin: auto;
        display: flex;
        flex-direction: column;
    }
}

@media (min-width: 1001px) {
    .virtues-recents-wrapper {
        width: 90%;
        margin: auto;
        display: flex;
        flex-direction: row;
    }
}

.recents-section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.featured-item-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px !important;
}

@media (max-width: 1000px) {
    .featured-item {
        width: 350px;
    }
}

@media (min-width: 1001px) {
  .featured-item {
    width: 300px;
  }
}

.event-img {
  height: 110px;
}

.featured-item {
  display: flex;
  height: auto;
  flex-direction: column;
  align-items: center;
  border-radius: 15px;
  border: solid 3px #2F5D3F;
}

.featured-item-title {
  padding: 8px;
  width: 100%;
  display: flex;
  justify-content: center;
  background-color: #D4C5B4;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
}

.featured-item-description {
  padding: 8px;
  width: 100%;
  display: flex;
  justify-content: center;
}

</style>