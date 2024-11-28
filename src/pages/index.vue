<template>
  <div class="page">
    <div style="margin-top: 30px;"></div>
    <img height="120px"
      src="@/assets/images/title-logo-no-bg.png"
      data-aos="zoom-in"
      data-aos-duration="1200"
    />

    <div style="margin-top: 60px;"></div>

    <div class="teddy-wrapper">
      <div class="teddy-img-row">
        <img src="@/assets/images/roosevelt.jpg"
          id="roosevelt-img"
          data-aos="fade-up-right"
          data-aos-duration="1200"
        />
        <p id="teddy-quote"
          data-aos="fade-up-left"
          data-aos-duration="1200"
        >
          {{ teddyQuote }}
        </p>
      </div>
      <p id="teddy-name"
        data-aos="fade-up"
        data-aos-duration="1200"
      >&ndash; Theodore Roosevelt</p>
    </div>

    <div style="margin-top: 40px;"></div>

    <p class="giant-header"
      data-aos="fade-up"
      data-aos-duration="1200"
    >Step Up. Step In.</p>

    <div style="margin-top: 30px;"></div>

    <hr id="divider" />
    
    <p class="main-text" id="introduction" v-html="introduction"></p>
    
    <hr id="divider" />

    <div class="featured-row">
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

const introduction = ref('We encourage all men to rise above a life of passivity and ignoble ease as a critic in the spectator stands of life and instead to embrace the grittiness of honorable action within the arena of their own lives.<br><br>We desire to forge ourselves and each other not only into good men of virtue and morals but into men who are good at being men as well.<br><br>Through regular, in-person meetups and monthly challenges we push each other to become husbands, fathers, brothers, sons, friends and citizens of the highest quality.')
const teddyQuote = ref('"It is not the critic who counts; not the man who points out how the strong man stumbles, or where the doer of deeds could have done them better. The credit belongs to the man who is actually in the arena, whose face is marred by dust and sweat and blood; who strives valiantly; who errs, who comes short again and again, because there is no effort without error and shortcoming; but who does actually strive to do the deeds; who knows great enthusiasms, the great devotions; who spends himself in a worthy cause; who at the best knows in the end the triumph of high achievement, and who at the worst, if he fails, at least fails while daring greatly, so that his place shall never be with those cold and timid souls who neither know victory nor defeat."')

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

@media (max-width: 900px) {
  .featured-row {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  
  .featured-item-wrapper {
    margin-bottom: 20px !important;
  }
}

@media (min-width: 901px) and (max-width: 1085px) {
  .featured-row {
    width: 85%;
    display: flex;
    flex-direction: row;
    justify-content: space-between !important;
    margin-bottom: 20px !important;
  }
}

@media (min-width: 1086px) {
  .featured-row {
    width: 70%;
    display: flex;
    flex-direction: row;
    justify-content: space-between !important;
    margin-bottom: 20px !important;
  }
}

@media (max-width: 1000px) {
  .arena-row {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}

@media (min-width: 1001px) {
  .arena-row {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
}

@media (max-width: 600px) {
  #arena-img {
    width: 200px;
  }
}

@media (min-width: 601px) and (max-width: 1000px) {
  #arena-img {
    width: 250px;
  }
}

@media (min-width: 1001px) {
  #arena-img {
    width: 300px;
  }
}

@media (max-width: 450px) {
  .teddy-wrapper {
    width: 90%;
  }

  #introduction {
    width: 90%;
    text-align: center;
    font-weight: bold;
  }

  #divider {
    width: 95%;
  }
}

@media (min-width: 451px) {
  .teddy-wrapper {
    width: 60%;
  }

  #introduction {
    width: 60%;
    text-align: center;
    font-weight: bold;
  }

  #divider {
    width: 65%;
  }
}

#divider {
  height: 2px;
  color: #2D2825;
  background: #2D2825;
  margin: 30px;
}

.teddy-wrapper {
  margin: 20px;
}

.teddy-img-row {
  display: block;
}

#teddy-quote, #teddy-name {
  color: #2D2825;
  font-family: 'SpecialElite';
  font-size: 17px;
}

#teddy-name {
  float: right;
  color: #2F5D3F !important;
  font-weight: bold;
  font-style: italic;
  margin-top: 10px;
}

#roosevelt-img {
  float: left;
  height: 150px;
  border: solid 5px #2F5D3F;
  margin: 0 15px 0 0;
}

.arena-row {
  margin: 15px 0;
}

#arena-img {
  margin: 15px;
  border-radius: 6px;
}

#motto {
  font-size: 24px;
  margin-bottom: 5px;
  background: linear-gradient(to right, #D4C5B4, #2F5D3F, #D4C5B4);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
}

.featured-item-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

@media (max-width: 450px) {
  .featured-item {
    width: 250px;
    /* height: 250px; */
  }
}

@media (min-width: 451px) {
  .featured-item {
    width: 350px;
    /* height: 200px; */
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
  border-radius: 6px;
  border: solid 1px #2F5D3F;
  box-shadow: #2F5D3F 4px 4px;
}

.featured-item-title {
  padding: 8px;
  width: 100%;
  display: flex;
  justify-content: center;
  background-color: #D4C5B4;
  border-top-left-radius: 6px;
  border-top-right-radius: 6px;
}

.featured-item-description {
  padding: 8px;
  width: 100%;
  display: flex;
  justify-content: center;
}

.chevron-btn {
  border-radius: 50%;
  color: #2D2825;
}

.chevron-btn:hover {
  cursor: pointer;
}

</style>