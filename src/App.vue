<script lang="ts">
import { defineComponent } from "vue";
import { lightTheme, darkTheme, NConfigProvider } from "naive-ui";
import ThemeChangeSwitch from "./components/ThemeChangeSwitch.vue";
import WelcomeBlock from "./components/WelcomeBlock.vue";
import AboutBlock from "./components/AboutBlock.vue";
import ExperienceBlock from "./components/ExperienceBlock.vue";
import NavBarNew from "./components/NavBarNew.vue";
import SocialLinks from "./components/SocialLinks.vue";

export default defineComponent({
  components: {
    NConfigProvider,
    WelcomeBlock,
    AboutBlock,
    ExperienceBlock,
    ThemeChangeSwitch,
    NavBarNew,
    SocialLinks,
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
    <NavBarNew />
    <SocialLinks />
    <ThemeChangeSwitch class="theme-changer-position" />
    <WelcomeBlock />
    <AboutBlock />
    <ExperienceBlock />
  </NConfigProvider>
</template>

<style>
html,
body {
  color: var(--background-color);
  background-color: var(--background-color);
  transition: background-color;
  overflow: hidden;
}
</style>
