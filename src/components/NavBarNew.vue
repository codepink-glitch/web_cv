<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  mounted() {
    document.addEventListener(
      "wheel",
      (event: WheelEvent) => {
        event.preventDefault();
        event.stopPropagation();

        const indexTo: number =
          this.allLinks.indexOf(this.currentLink) + (event.deltaY > 0 ? 1 : -1);

        if (indexTo > this.allLinks.length || indexTo < 0) return;

        this.moveTo(this.allLinks[indexTo]);
      },
      { passive: false }
    );

    document.addEventListener(
      "touchmove",
      (event: TouchEvent) => {
        event.preventDefault();
        event.stopPropagation();
      },
      { passive: false }
    );
  },
  data() {
    return {
      currentLink: "home",
      allLinks: ["home", "about-block", "experience-block"],
    };
  },
  methods: {
    moveTo(value: string) {
      if (value === "home") {
        window.scrollTo({ top: 0, behavior: "smooth" });
      } else {
        const targetEl: HTMLElement | null = document.getElementById(value);

        if (targetEl === null) return;

        targetEl.scrollIntoView({ behavior: "smooth", block: "start" });
      }
      this.currentLink = value;
    },
  },
});
</script>

<template>
  <div class="navbar__container navbar-position">
    <span
      :class="(currentLink === 'home' ? 'active ' : '') + 'hoverable text'"
      @click="moveTo('home')"
      id="home-link"
      >Home</span
    >
    <span
      :class="
        (currentLink === 'about-block' ? 'active ' : '') + 'hoverable text'
      "
      @click="moveTo('about-block')"
      id="about-block-link"
      >About</span
    >
    <span
      class="hoverable text"
      :class="
        (currentLink === 'experience-block' ? 'active ' : '') + 'hoverable text'
      "
      @click="moveTo('experience-block')"
      id="experience-block-link"
      >Experience</span
    >
  </div>
</template>

<style scoped>
.navbar__container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-end;
}

@media screen and (min-width: 601px) {
  .navbar-position {
    position: fixed;
    top: 10%;
    right: 3%;
  }

  .text {
    font-size: 1.5rem;
  }
}

@media screen and (max-width: 600px) {
  .navbar-position {
    position: fixed;
    top: 1.5%;
    right: 1%;
    backdrop-filter: blur(2px);
  }

  .text {
    font-size: 1rem;
  }
}
.text {
  color: var(--text-color) !important;
  opacity: 0.5;
  font-family: v-mono;
  transition: 0.3s ease-in-out;
}
</style>
