<script lang="ts">
import { defineComponent } from "vue";
import { lightTheme, darkTheme, NConfigProvider } from "naive-ui";
import NavBar from "./components/NavBar.vue";
import WelcomeBlock from "./components/WelcomeBlock.vue";
import AboutBlock from "./components/AboutBlock.vue";
import ExperienceBlock from "./components/ExperienceBlock.vue";

export default defineComponent({
  components: {
    NConfigProvider,
    NavBar,
    WelcomeBlock,
    AboutBlock,
    ExperienceBlock,
  },
  data() {
    return {
      theme: lightTheme,
    };
  },
  methods: {
    changeTheme(value: boolean) {
      this.theme = value ? darkTheme : lightTheme;
    },
  },
});
</script>

<template>
  <NConfigProvider :theme="theme">
    <NavBar @themeChange="changeTheme" class="nav-bar" />
    <WelcomeBlock />
    <AboutBlock />
    <ExperienceBlock />
  </NConfigProvider>
</template>

<style>
.nav-bar {
  position: fixed;
  left: 0;
  top: 0;
  width: 100vw;
  z-index: 100;
  backdrop-filter: blur(2px);
}

html,
body {
  color: var(--background-color);
  background-color: var(--background-color);
  transition: background-color;
}
</style>
