<template>
  <div class="component">
    <div class="resource-list-wrapper">
      <button @click="decrement()" style="align-self: center;" :disabled="currentPage === 0">
        <v-icon size="35" :color="currentPage === 0 ? 'transparent' : ''">mdi-chevron-left</v-icon>
      </button>

      <div class="resource-list-column" v-if="displayedResources.length > 0">
        <div class="resource-row"
          @click="openResLink(res.url)"
          v-for="(res, index) in displayedResources"
          :key="index"
          data-aos="fade-up"
          data-aos-duration="1200"
          data-aos-delay="150"
        >
          <img :src="res.image" class="resource-image" />
          <div class="resource-info">
            <h3 class="resource-title item-title">{{ res.title }}</h3>
            <p class="medium-text">{{ res.author }}</p>
            <p class="resource-blurb small-text">{{ res.blurb }}</p>
          </div>
        </div>
      </div>
      
      <button @click="increment()" style="align-self: center;" :disabled="currentPage >= maxPage">
        <v-icon size="35" :color="currentPage === maxPage ? 'transparent' : ''">mdi-chevron-right</v-icon>
      </button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed, onMounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'

onMounted(() => {
  AOS.init()
  windowWidth.value = window.innerWidth
  window.addEventListener('resize', () => {
    windowWidth.value = window.innerWidth
  })
})

const props = defineProps(['resources'])

let windowWidth = ref(0)
const currentPage = ref(0)

const resPerPage = ref(3)
const maxPage = computed(() => Math.ceil(props.resources.length / resPerPage.value) - 1)

const displayedResources = computed(() => {
  const start = currentPage.value * resPerPage.value
  return props.resources.slice(start, start + resPerPage.value)
})

function increment() {
  if (currentPage.value < maxPage.value) {
    currentPage.value++
  }
}

function decrement() {
  if (currentPage.value > 0) {
    currentPage.value--
  }
}

function openResLink(url: string) {
  window.open(url)
}
</script>

<style>
@import '@/styles/style.css';

.resource-list-wrapper {
  display: flex;
  align-items: start;
}

.resource-list-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

@media (max-width: 450px) {
  .resource-row {
    flex-direction: column;
  }
}

@media (min-width: 451px) {
  .resource-row {
    flex-direction: row;
  }
}

.resource-row {
  display: flex;
  align-items: center;
  padding: 8px;
}

.resource-row:hover {
  background-color: #B8B8B833;
  cursor: pointer;
}

.resource-image {
  width: 80px;
  height: auto;
  margin-right: 15px;
}

.resource-info {
  display: flex;
  flex-direction: column;
}

.resource-title {
  font-weight: bold;
  margin: 0;
}

.resource-blurb {
  font-size: 0.9em;
  color: #555;
}

</style>