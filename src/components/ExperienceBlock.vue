<script lang="ts">
import { defineComponent } from "vue";
import ExperienceItem from "./ExperienceItem.vue";

export default defineComponent({
  components: { ExperienceItem },
  data() {
    return {
      experienceItems: [
        {
          id: 1,
          company: "St. Petersburg Information and Analytical Center",
          position: "Full-stack software engineer",
          description: [
            "Write modern, performant, maintainable code for a diverse array of internal projects.",
            "Work with a variety of different languages, platforms and frameworks such as JavaScript," +
              " TypeScript, Vue, React, Java and Spring framework",
          ],
          startDate: "11-2022",
          endDate: "present",
        },
        {
          id: 2,
          company: "Inside LTD",
          position: "QA Automation Engineer",
          description: [
            "Writing scripts for test database population.",
            "Unit test writing.",
            "UI test writing with selenium.",
          ],
          startDate: "09-2021",
          endDate: "11-2021",
        },
      ],
    };
  },
});
</script>

<template>
  <div class="experience__container" id="experience-block">
    <span class="header-text">Where i've worked</span>
    <div
      v-for="item in experienceItems"
      :key="item.id"
      class="experience-item__container"
    >
      <ExperienceItem
        :company="item.company"
        :position="item.position"
        :description="item.description"
        :start-date="item.startDate"
        :end-date="item.endDate"
      />
    </div>
  </div>
</template>

<style scoped>
.header-text {
  font-weight: 500;
  color: var(--text-color);
  transition: color 0.5s linear;
  font-family: v-sans, v-mono;
  padding: 0 2rem;
}

@media screen and (max-width: 700px) {
  .header-text {
    font-size: 1.2rem;
  }

  #experience-block {
    scroll-margin-top: 5vh;
  }

  .experience__container {
    width: 90wv;
  }
}

@media screen and (min-width: 601px) {
  .header-text {
    font-size: 2rem;
  }

  #experience-block {
    scroll-margin-top: 20vh;
  }

  .experience__container {
    width: 60vw;
  }
}

.experience__container {
  height: fit-content;
  margin: auto;
  margin-bottom: 30vh;
  padding: 1rem;
}

.experience-item__container {
  margin: 1rem;
}
</style>
