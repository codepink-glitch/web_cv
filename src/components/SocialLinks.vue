<script lang="ts">
import { defineComponent } from "vue";
import { NIcon } from "naive-ui";
import {
  BrandLinkedin,
  BrandGithub,
  BrandTelegram,
  MailForward,
} from "@vicons/tabler";

export default defineComponent({
  components: { NIcon, BrandLinkedin, BrandGithub, BrandTelegram, MailForward },
  methods: {
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
  <div class="social__container">
    <NIcon size="26" class="icon-container">
      <MailForward class="hoverable icon-color" @click="openMail" />
    </NIcon>
    <NIcon size="26" class="icon-container">
      <BrandLinkedin class="hoverable icon-color" @click="openLinkedin" />
    </NIcon>
    <NIcon size="26" class="icon-container">
      <BrandGithub class="hoverable icon-color" @click="openGithub" />
    </NIcon>
    <NIcon size="26" class="icon-container">
      <BrandTelegram class="hoverable icon-color" @click="openTelegram" />
    </NIcon>
  </div>
</template>

<style scoped>
.social__container {
  position: fixed;
  bottom: 1.5%;
  right: 3%;
}

.icon-container {
  padding: 0.3rem;
}

.icon-color {
  color: var(--text-color);
}
</style>
