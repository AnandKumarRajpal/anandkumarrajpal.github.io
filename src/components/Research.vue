<template>
    <v-container id="research">
        <v-row class="main-container">
            <v-col class="px-0 py-0">
                <v-row class="mx-0 mb-4 my-0 align-center">
                    <p class="code-style darkText section-heading my-0">02.02 - Research</p>
                    <v-divider class="ml-4"></v-divider>
                </v-row>
                <v-row class="mx-0 mb-4 my-0 align-center">
                    <p class="code-style darkText section-heading my-0">02.02.01 - Peer-Reviewed Conference Papers</p>
                    <v-divider class="ml-4"></v-divider>
                </v-row>
                <v-row v-for="paper in papersList" :key="paper.id" class="mb-4 mx-0 my-0">
                  <v-card flat class="darkLight">
                    <v-card-text class="card-text">
                      <p v-html="getPaperTitle(paper)"></p>
                      <div>
                        <v-divider></v-divider>
                        <p class="mt-4 mb-0" v-html="getPaperLinks(paper)"></p>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-row>
                <v-row class="mx-0 my-4 my-0 align-center">
                    <p class="code-style darkText section-heading my-0">02.02.02 - Posters</p>
                    <v-divider class="ml-4"></v-divider>
                </v-row>
                <v-row v-for="paper in postersList" :key="paper.id" class="mb-4 mx-0 my-0">
                  <v-card flat class="darkLight">
                    <v-card-text class="card-text">
                      <p v-html="getPaperTitle(paper)"></p>
                      <div>
                        <v-divider v-if="!!getPaperLinks(paper)"></v-divider>
                        <p class="mt-4 mb-0" v-html="getPaperLinks(paper)"></p>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-row>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
// import AchievementCard from "./AchievementCard.vue";
import { research } from "@/data";

export default {
  name: "c-research",
  components: {},
  methods: {
    getPaperTitle(paper) {
      let authors = paper["Authors"].map(author => {
        if (author === "Anand Kumar") {
          return `<span class="font-weight-bold darkText">${author}</span>`;
        }
        return author;
      });

      let title = `<span class="font-italic">${paper["Title"]}</span>`;

      return authors.join(", ") + ". " + paper["Year"] + ". " + title + ". " + paper["Venue"];
    },
    getPaperLinks(paper) {
      let links = [];
      if (paper["PDF"]) {
        links.push(`<a href="papers/${paper["PDF"]}" target="_blank" class="link">PDF</a>`);
      }
      if (paper["Video"]) {
        links.push(`<a href="${paper["Video"]}" target="_blank" class="link">Video</a>`);
      }
      if (paper["DOI"]) {
        links.push(`<a href="${paper["DOI"]}" target="_blank" class="link">DOI</a>`);
      }
      return links.join(" | ");
    },
  },
  computed: {
    papersList() {
      return research
        .filter((item) => item.Type === "Peer-Reviewed Conference Paper")
        .slice()
        .reverse();
    },
    postersList() {
      return research
        .filter((item) => item.Type === "Poster")
        .slice()
        .reverse();
    },
  },
};
</script>

<style>
</style>