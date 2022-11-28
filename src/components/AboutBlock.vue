<script lang="ts">
import { defineComponent } from "vue";
import { NIcon } from "naive-ui";
import { Java, Leaf, Vuejs, NodeJs, Docker } from "@vicons/fa";
import { Javascript24Regular } from "@vicons/fluent";
import { Sql, DatabaseMongodb } from "@vicons/carbon";
import avatar from "../assets/img/me.jpeg";

export default defineComponent({
  components: {
    NIcon,
    Java,
    Leaf,
    Javascript24Regular,
    Vuejs,
    NodeJs,
    Docker,
    Sql,
    DatabaseMongodb,
  },
  data() {
    return {
      avatar,
      descriptionText:
        "I enjoy creating things that makes people life easier. \n" +
        "For over a year creating and maintaining apps with java and javascript. \n " +
        "Love writing tests and working in team. ",
      preTechnologiesText:
        "Here's technologies I’ve been working with recently:",
    };
  },
});
</script>

<template>
  <div class="about__container" id="about-block">
    <div class="content__container">
      <div class="text__container">
        <h2 class="text header-text">About me</h2>
        <span class="text regular-text text-whitespace">{{
          descriptionText
        }}</span>
        <div class="technologies__container">
          <span class="text regular-text">{{ preTechnologiesText }}</span>
          <div class="technologies-wrapper">
            <div class="technologies__list">
              <div class="technology">
                <NIcon size="18">
                  <Java class="text" />
                </NIcon>
                <span class="text">Java</span>
              </div>
              <div class="technology">
                <NIcon size="18">
                  <Leaf class="text" />
                </NIcon>
                <span class="text">Spring</span>
              </div>
            </div>
            <div class="technologies__list">
              <div class="technology">
                <NIcon size="18">
                  <Javascript24Regular class="text" style="margin-top: 2px" />
                </NIcon>
                <span class="text">JavaScript</span>
              </div>
              <div class="technology">
                <NIcon size="18">
                  <Vuejs class="text" />
                </NIcon>
                <span class="text">Vue.js</span>
              </div>
              <div class="technology">
                <NIcon size="18">
                  <NodeJs class="text" />
                </NIcon>
                <span class="text">Node.js</span>
              </div>
            </div>
            <div class="technologies__list">
              <div class="technology">
                <NIcon size="18">
                  <Docker class="text" style="margin-top: 2px" />
                </NIcon>
                <span class="text">Docker</span>
              </div>
              <div class="technology">
                <NIcon size="18">
                  <Sql class="text" style="margin-top: 2px" />
                </NIcon>
                <span class="text">SQL</span>
              </div>
              <div class="technology">
                <NIcon size="18">
                  <DatabaseMongodb class="text" />
                </NIcon>
                <span class="text">MongoDB</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="img__container">
        <img class="responsive" :src="avatar" />
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  --width: 70vw;
}

.technologies-wrapper {
  display: inline-flex;
  gap: 4vh;
}

.technology {
  display: flex;
  gap: 1vh;
}

.technologies__list {
  margin-top: 0.5rem;
}

.technologies__container {
  margin-top: 1rem;
}

.text__container {
  padding: 4vh;
}

@media screen and (max-width: 600px) {
  .content__container {
    flex-direction: column;
    justify-content: center;
    align-items: center;
    display: flex;
  }

  #about-block {
    scroll-margin-top: 5vh;
  }
}

@media screen and (min-width: 601px) {
  .content__container {
    display: inline-flex;
  }

  #about-block {
    scroll-margin-top: 15vh;
  }
}

.img__container {
  display: flex;
  align-items: center;
  justify-content: center;
}

img {
  border-radius: 50%;
}

.responsive {
  width: 100%;
  max-width: 25vw;
}

.avatar__container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.text-whitespace {
  white-space: pre-line;
}

.about__container {
  width: var(--width);
  height: fit-content;
  margin: auto;
  margin-top: 37vh;
  margin-bottom: 37vh;
  padding: 5vh;
  max-width: 70%;
}

.text {
  color: var(--text-color);
  transition: color 0.5s linear;
}

.regular-text {
  font-family: v-sans, v-mono;
  font-weight: 400;
  font-size: 1rem;
}

.header-text {
  font-family: v-sans, v-mono;
  font-weight: 500;
  font-size: 2.5rem;
}
</style>
