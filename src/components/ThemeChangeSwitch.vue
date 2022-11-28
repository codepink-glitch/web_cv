<script lang="ts">
import { defineComponent, ref } from "vue";
import { NSwitch, NIcon } from "naive-ui";
import { DarkModeOutlined, LightModeOutlined } from "@vicons/material";

export default defineComponent({
  components: { NSwitch, NIcon, DarkModeOutlined, LightModeOutlined },
  data() {
    return {
      active: ref(false),
      darkThemeTextColor: "aliceblue",
      lightThemeTextColor: "rgb(14, 16, 16)",
      darkThemeBackgroundColor: "#181a19",
      lightThemeBackgroundColor: "rgb(245, 240, 240)",
      darkThemeBoxShadow: "20px 20px 40px #141615, -20px -20px 40px #1c1e1d",
      lightThemeBoxShadow: "20px 20px 40px #d0cccc, -20px -20px 40px #ffffff",
    };
  },
  methods: {
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
  <NSwitch size="small" @update:value="changeTheme">
    <template #checked>
      <NIcon size="16">
        <DarkModeOutlined class="icon" />
      </NIcon>
    </template>
    <template #unchecked>
      <NIcon size="16">
        <LightModeOutlined class="icon" />
      </NIcon>
    </template>
  </NSwitch>
</template>

<style scoped>
.icon {
  color: var(--text-color);
  transition: color 0.3s linear;
}
</style>
