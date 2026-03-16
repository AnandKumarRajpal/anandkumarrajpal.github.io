<template>
  <v-container id="achievements">
    <v-row class="main-container">
      <v-col class="px-0 py-0">
        <v-row class="mx-0 mb-4 my-0 align-center">
          <p class="code-style darkText section-heading my-0">02.05 - Achievements</p>
          <v-divider class="ml-4"></v-divider>
        </v-row>
        <v-row class="mx-0 my-0">
          <v-col
            :key="item.id"
            v-for="item in achievements"
            cols="12"
            sm="6"
            lg="4"
          >
            <c-achievement-card
              class="mx-auto darkLight"
              :title="item.title"
              :description="item.description"
              :linkTitle="item.linkTitle"
              :link="item.link"
              :iconLink="item.iconLink"
              :noFilter="item.noFilter"
            ></c-achievement-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import AchievementCard from "./AchievementCard.vue";
import { achievements } from "@/data";

export default {
  name: "c-achievements",
  components: {
    cAchievementCard: AchievementCard,
  },
  computed: {
    achievements() {
      return [...achievements].reverse();
    },
  },
};
</script>

<style>
</style>