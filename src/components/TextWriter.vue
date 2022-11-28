<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    preText: String,
    displayTextArray: Array<String>,
  },
  data() {
    return {
      typeValue: "",
      typeStatus: false,
      typingSpeed: 100,
      erasingSpeed: 100,
      newTextDelay: 2000,
      displayTextArrayIndex: 0,
      charIndex: 0,
    };
  },
  mounted() {
    setTimeout(this.typeText, this.newTextDelay + 200);
  },
  methods: {
    typeText() {
      if (!this.displayTextArray) {
        return;
      }

      if (
        this.charIndex <
        this.displayTextArray[this.displayTextArrayIndex].length
      ) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue += this.displayTextArray[
          this.displayTextArrayIndex
        ].charAt(this.charIndex);
        this.charIndex += 1;
        setTimeout(this.typeText, this.typingSpeed);
      } else {
        this.typeStatus = false;
        setTimeout(this.eraseText, this.newTextDelay);
      }
    },
    eraseText() {
      if (!this.displayTextArray) {
        return;
      }

      if (this.charIndex > 0) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue = this.displayTextArray[
          this.displayTextArrayIndex
        ].substring(0, this.charIndex - 1);
        this.charIndex -= 1;
        setTimeout(this.eraseText, this.erasingSpeed);
      } else {
        this.typeStatus = false;
        this.displayTextArrayIndex += 1;
        if (this.displayTextArrayIndex >= this.displayTextArray.length)
          this.displayTextArrayIndex = 0;
        setTimeout(this.typeText, this.typingSpeed + 1000);
      }
    },
  },
});
</script>

<template>
  <div class="container">
    <h1>
      <span v-show="!!preText" class="text">{{ preText }}</span>
      <span type="info" class="typed-text">{{ typeValue }}</span>
      <span type="info" class="blinking-cursor">|</span>
      <span class="cursor" :class="{ typing: typeStatus }">&nbsp;</span>
    </h1>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-top: -6vh;
}

.text {
  transition: color 0.5s linear;
  color: var(--text-color);
}

.text,
.typed-text {
  font-size: 5vh;
  font-family: v-mono;
  font-weight: 400;
}

h1,
.typed-text {
  color: #d2b94b;
}

.blinking-cursor {
  font-size: 5vh;
  color: #d2b94b;
  animation: 1s blink step-end infinite;
}

@keyframes blink {
  from,
  to {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
}
</style>
