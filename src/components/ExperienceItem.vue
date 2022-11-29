<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    company: String,
    position: String,
    description: Array<String>,
    startDate: String,
    endDate: String,
  },
});
</script>

<template>
  <div class="experience-item">
    <div class="experience-header">
      <div class="header-position-company">
        <span class="text">{{ position + "@" + company }}</span>
      </div>
      <div class="header-dates">
        <span class="text">{{ startDate + " to " + endDate }}</span>
      </div>
    </div>
    <hr class="divider" />
    <div class="experience-content">
      <div class="experience-description">
        <ul style="margin-left: -1rem">
          <!-- eslint-disable-next-line vue/require-v-for-key -->
          <li v-for="line in description" class="text">{{ line }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style>
.experience-header {
  display: flex;
  justify-content: space-between;
  margin-left: 1rem;
  margin-right: 1rem;
}

.experience-description {
  padding: 0;
}

hr.divider {
  transition: color 0.5s linear;
  border-top: 1px solid var(--text-color);
}

@media screen and (max-width: 700px) {
  .experience-item {
    width: 70vw;
  }
}

@media screen and (min-width: 701px) {
  .experience-item {
    width: 50vw;
  }
}

.experience-item {
  border-radius: 2vw;
  box-shadow: var(--box-shadow);
  transition: opacity 0.5s ease-in-out;
  padding: 1rem;
}

.text {
  color: var(--text-color);
  transition: color 0.5s linear;
  font-family: v-sans, v-mono;
  font-weight: 400;
}
</style>
