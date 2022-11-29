<script lang="ts">
import { defineComponent } from "vue";
import { DarkModeOutlined, LightModeOutlined } from "@vicons/material";
import { NIcon } from "naive-ui";

export default defineComponent({
  components: { NIcon, DarkModeOutlined, LightModeOutlined },
  data() {
    return {
      mode: "light",
      darkThemeTextColor: "aliceblue",
      lightThemeTextColor: "rgb(14, 16, 16)",
      darkThemeBackgroundColor: "#181a19",
      lightThemeBackgroundColor: "rgb(245, 240, 240)",
      darkThemeBoxShadow: "20px 20px 40px #141615, -20px -20px 40px #1c1e1d",
      lightThemeBoxShadow: "20px 20px 40px #d0cccc, -20px -20px 40px #ffffff",
    };
  },
  methods: {
    changeMode(mode: string) {
      this.mode = mode;
      this.changeTheme(mode === "dark");
    },
    changeTheme(value: boolean) {
      const root: HTMLElement | null = document.querySelector(":root");
      this.$emit("themeChange", value);
      if (root === null) {
        return;
      }
      root.style.setProperty(
        "--background-color",
        value ? this.darkThemeBackgroundColor : this.lightThemeBackgroundColor
      );
      root.style.setProperty(
        "--text-color",
        value ? this.darkThemeTextColor : this.lightThemeTextColor
      );
      root.style.setProperty(
        "--box-shadow",
        value ? this.darkThemeBoxShadow : this.lightThemeBoxShadow
      );
    },
  },
});
</script>

<template>
  <div class="theme-switcher-position">
    <NIcon size="30">
      <DarkModeOutlined
        v-if="mode === 'light'"
        class="icon"
        @click="changeMode('dark')"
      />
      <LightModeOutlined v-else class="icon" @click="changeMode('light')" />
    </NIcon>
  </div>
</template>

<style scoped>
.theme-switcher-position {
  position: fixed;
  bottom: 1.5%;
  left: 3%;
}
.icon {
  color: var(--text-color);
  transition: color 0.3s linear;
  opacity: 0.5;
  cursor: pointer;
}

.icon:hover {
  opacity: 1;
}
</style>
