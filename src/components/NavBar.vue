<script lang="ts">
import { defineComponent } from "vue";
import ThemeChangeSwitch from "./ThemeChangeSwitch.vue";
import { NSpace, NIcon } from "naive-ui";
import {
  BrandLinkedin,
  BrandGithub,
  BrandTelegram,
  MailForward,
} from "@vicons/tabler";

export default defineComponent({
  components: {
    NSpace,
    NIcon,
    BrandLinkedin,
    BrandGithub,
    BrandTelegram,
    MailForward,
    ThemeChangeSwitch,
  },
  methods: {
    themeChange(value: boolean) {
      this.$emit("themeChange", value);
    },
    moveTo(value: string) {
      if (value === "home") {
        window.scrollTo({ top: 0, behavior: "smooth" });
      } else {
        document
          .getElementById(value)
          ?.scrollIntoView({ behavior: "smooth", block: "start" });
      }
    },
    openLink(uri: string) {
      window.open(uri, "_blank")?.focus();
    },
    openLinkedin() {
      this.openLink("https://www.linkedin.com/in/egor-vasiliev-377814234/");
    },
    openGithub() {
      this.openLink("https://github.com/codepink-glitch");
    },
    openTelegram() {
      this.openLink("https://t.me/codepink");
    },
    openMail() {
      this.openLink("mailto:em.vasiliev@outlook.com");
    },
  },
});
</script>

<template>
  <NSpace class="spacer" justify="space-between">
    <div class="switch-wrapper">
      <ThemeChangeSwitch @themeChange="themeChange" />
    </div>
    <div class="menu-wrapper">
      <span class="hoverable" @click="moveTo('home')">Home</span>
      <span class="hoverable" @click="moveTo('about-block')">About</span>
      <span class="hoverable" @click="moveTo('experience-block')"
        >Experience</span
      >
      <div class="container-social">
        <NIcon size="24">
          <MailForward class="hoverable" @click="openMail" />
        </NIcon>
        <NIcon size="22">
          <BrandLinkedin class="hoverable" @click="openLinkedin" />
        </NIcon>
        <NIcon size="22">
          <BrandGithub class="hoverable" @click="openGithub" />
        </NIcon>
        <NIcon size="22">
          <BrandTelegram class="hoverable" @click="openTelegram" />
        </NIcon>
      </div>
    </div>
  </NSpace>
</template>

<style scoped>
.switch-wrapper {
  padding-top: 0.1rem;
  padding-left: 1rem;
}
.menu-wrapper {
  display: inline-flex;
  padding-top: 0.1rem;
  padding-right: 1rem;
  padding-right: 1rem;
}

.menu-wrapper > * {
  margin: 0 0.5rem 0 0.5rem;
}

span {
  font-family: v-sans, v-mono;
  font-weight: 400;
  font-size: 1rem;
}

.hoverable {
  color: var(--text-color) !important;
  opacity: 0.5;
  cursor: pointer;
  transition: 0.3s ease-in-out;
}

.spacer {
  display: flex;
  max-width: 100%;
}

.spacer button {
  padding-bottom: 10px;
}

.brand-icon {
  color: var(--text-color) !important;
  opacity: 0.5;
  cursor: pointer;
}

.hoverable:hover,
.hoverable:active,
.hoverable.active {
  opacity: 1;
}

.container-social {
  column-gap: 0.5rem;
  display: flex;
  justify-content: space-between;
  padding-top: 0.15rem;
}
</style>
