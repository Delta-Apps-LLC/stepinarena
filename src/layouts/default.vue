<template>
  <v-app id="app">
    <v-app-bar id="app-bar" flat>
      <v-app-bar-title>
        <RouterLink to="/">
          <img id="logo-btn" src="@/assets/images/img-logo-no-bg.png" />
        </RouterLink>
      </v-app-bar-title>

      <div v-if="windowWidth > 800">
        <RouterLink class="router-link"
          v-for="(btn, i) in navBtns"
          :key="i"
          :to="btn.to"
        >{{ btn.title }}</RouterLink>
      </div>

      <v-menu v-if="windowWidth <= 800">
        <template v-slot:activator="{ props }">
          <v-btn icon v-bind="props">
            <v-icon size="30">mdi-menu</v-icon>
          </v-btn>
        </template> 

        <v-list style="display: flex; flex-direction: column;">
          <RouterLink class="router-link"
            v-for="(btn, i) in navBtns"
            :key="i"
            :to="btn.to"
          >{{ btn.title }}</RouterLink>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      <RouterView />
    </v-main>
    
  </v-app>
</template>

<script lang="ts" setup>
import { RouterLink, RouterView, useRouter, useRoute } from 'vue-router'
import { ref, onMounted } from 'vue';

const router = useRouter();
const route = useRoute();
const windowWidth = ref(0);

onMounted(() => {
  windowWidth.value = window.innerWidth;
  window.addEventListener('resize', () => {
    windowWidth.value = window.innerWidth;
  });
});

const navBtns = [
  { title: 'Home', to: '/' },
  { title: 'Articles', to: '/articles' },
  { title: 'Events', to: '/events' },
  { title: 'Resources', to: '/resources' },
  { title: 'Store', to: '/store' },
  { title: 'Contact', to: '/contact' },
];

</script>

<style scoped>
@import '@/styles/style.css';

#app-bar {
  width: 100vw !important;
  position: fixed !important;
  padding: 6px;
  display: flex;
  flex-direction: row;
  background-color: #F3F7F5;
  justify-content: space-between;
  align-items: center;
  z-index: 9999;
}

#logo-btn {
  height: 60px;
}

</style>