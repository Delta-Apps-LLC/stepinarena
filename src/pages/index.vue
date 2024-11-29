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

    <div style="margin-top: 50px;"></div>

    <div class="join-newsletter-wrapper"
      data-aos="fade-up"
      data-aos-duration="1200"
    >
      <p class="big-header" style="font-family: 'SpecialElite'; text-align: center;">Join Our Newsletter</p>
      <div id="newsletter-form">
        <input class="newsletter-input"
          v-model="name"
          type="text"
          required
          placeholder="Name"
        />
        <input class="newsletter-input"
          v-model="email"
          type="email"
          required
          placeholder="Email"
        />
      </div>
      <v-btn class="submit-btn" id="newsletter-btn" flat>Submit</v-btn>
    </div>
    
    <div style="margin-top: 70px;"></div>
    
    <hr id="divider"
      data-aos="fade-up"
      data-aos-duration="1200"
    />
    <p class="main-text"
      id="introduction"
      v-html="introduction"
      data-aos="fade-up"
      data-aos-duration="1200"
    ></p>
    <hr id="divider"
      data-aos="fade-up"
      data-aos-duration="1200"
    />
    
    <div style="margin-top: 70px;"></div>

    <VirtuesRecents />

    <div style="margin-top: 60px;"></div>

    <p class="emerson-quote"
      data-aos="fade-up-right"
      data-aos-duration="1200"
    >
      “We need men who not only have values and principles, but who stand up for their values and principles.”
    </p>
    <p class="emerson-quote-name"
      data-aos="fade-up-left"
      data-aos-duration="1200"
    >&ndash; Emerson Parker, Founder of The Arena</p>

    <div style="margin-top: 60px;"></div>

    <div>
      <p class="big-header header-font"
        data-aos="fade-up"
        data-aos-duration="1200"
      >Band Together with Other:</p>

      <ul class="check-list">
        <li class="check-list-item"
          data-aos="fade-right"
          data-aos-duration="1200"
        >
          <v-icon>mdi-checkbox-outline</v-icon>
          Men of values and principles
        </li>
        <li class="check-list-item"
          data-aos="fade-left"
          data-aos-duration="1200"
        >
          <v-icon>mdi-checkbox-outline</v-icon>
          Autonomous masters of skills
        </li>
        <li class="check-list-item"
          data-aos="fade-right"
          data-aos-duration="1200"
        >
          <v-icon>mdi-checkbox-outline</v-icon>
          Strong protectors and providers
        </li>
        <li class="check-list-item"
          data-aos="fade-left"
          data-aos-duration="1200"
        >
          <v-icon>mdi-checkbox-outline</v-icon>
          Men of community and service
        </li>
        <li class="check-list-item"
          data-aos="fade-right"
          data-aos-duration="1200"
        >
          <v-icon>mdi-checkbox-outline</v-icon>
          Active, enthusiastic participants of life
        </li>
      </ul>
    </div>

    <div style="margin-top: 60px;"></div>

    <p class="large-text fight-back"
      data-aos="fade-up"
      data-aos-duration="1200"
    >
      In a day and age where success equals money, happiness means pleasure, 
      and life is increasingly lived online, members of The Arena have chosen to fight back.
    </p>

    <div style="margin-top: 60px;"></div>

    <p class="giant-header"
      style="font-family: 'CrimsonText';"
      data-aos="fade-up"
      data-aos-duration="1200"
    >Will You?</p>
    <div id="newsletter-form"
      data-aos="fade-up"
      data-aos-duration="1200"
    >
      <input class="newsletter-input"
        v-model="name"
        type="text"
        required
        placeholder="Name"
      />
      <input class="newsletter-input"
        v-model="email"
        type="email"
        required
        placeholder="Email"
      />
    </div>
    <v-btn class="submit-btn"
      id="newsletter-btn"
      flat
      data-aos="fade-up"
      data-aos-duration="1200"
    >Submit</v-btn>
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

let name = ref('')
let email = ref('')

</script>

<style scoped>
@import '@/styles/style.css';


@media (max-width: 600px) {
  #newsletter-form {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .fight-back {
    font-weight: bold;
    text-align: center;
    width: 90%;
  }
}

@media (min-width: 601px) {
  #newsletter-form {
    display: flex;
    flex-direction: row;
    gap: 10px;
  }

  .fight-back {
    font-weight: bold;
    text-align: center;
    width: 60%;
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
    margin: 50px 0;
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
    margin: 50px 0;
  }

  #divider {
    width: 65%;
  }
}

#divider {
  height: 2px;
  color: #2D2825;
  background: #2D2825;
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

.join-newsletter-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  border: solid 3px #2F5D3F;
  border-radius: 20px;
  padding: 30px 40px;
}

.newsletter-input {
  padding: 6px 10px;
  font-family: 'CrimsonText';
  border: solid 2px #2F5D3F;
  border-radius: 20px;
}

#newsletter-btn {
  width: 100px;
  margin: 10px auto 0 auto;
}

.emerson-quote {
  font-family: 'SpecialElite';
  font-size: 20px;
  color: #2D2825;
}

.emerson-quote-name {
  font-family: 'AbrilFatface';
  letter-spacing: 1.2px;
  color: #2F5D3F;
}

.check-list {
  list-style: none;
  padding: 10px;
  font-family: 'SpecialElite';
  color: #2D2825;
  font-size: 18px;
}

.check-list-item {
  padding: 3px;
}

</style>