<script lang="ts">
import { defineComponent } from "vue";
import TextWriter from "./TextWriter.vue";

export default defineComponent({
  components: { TextWriter },
  data() {
    return {
      preText: "And i'm a ",
      displayTextArray: [
        "full-stack developer",
        "backend developer",
        "frontend developer",
      ],
      aboutText: `I'm specializing in building and supporting high load web applications and services.`,
    };
  },
});
</script>

<template>
  <div class="about__container">
    <h3 class="font-style">Hi, My name is</h3>
    <h1 class="font-style name-margin">Egor Vasilyev.</h1>
    <div class="text-writer-wrapper">
      <TextWriter :pre-text="preText" :display-text-array="displayTextArray" />
    </div>
    <div class="description-wrapper">
      <span class="font-style">{{ aboutText }}</span>
    </div>
  </div>
</template>

<style scoped>
* {
  --width: 70vw;
}

@media screen and (max-width: 700px) {
  .text-writer-wrapper {
    height: 30vh;
  }
}

.about__container {
  width: var(--width);
  height: fit-content;
  margin: auto;
  margin-top: 25vh;
  padding: 5vh;
  max-width: 90%;
}

.name-margin {
  margin-top: -2vh;
}

.description-wrapper {
  width: calc(var(--width) / 1.5);
  max-width: 80%;
}

h1 {
  font-size: 5vh;
}

h3 {
  font-size: 2vh;
}

.font-style {
  color: var(--text-color);
  transition: color 0.5s linear;
  font-family: v-mono;
  font-weight: 400;
}
</style>
