<template>
  <v-container id="about">
    <v-row class="main-container align-center justify-center">
      <v-col class="px-0 py-0">
        <v-row class="mx-0 mb-4 my-0 align-center">
          <p class="code-style darkText section-heading my-0">01 - About Me</p>
          <v-divider class="ml-4"></v-divider>
        </v-row>

        <p>
          Hi! 👋 I'm Anand Kumar, a Software Development Engineer at Veeam Software. I hold an MSc in Computer Science (Thesis) from the University of Calgary, where I worked under Aditya Shekhar Nittala.
        </p>
        <p>
          I'm passionate about solving complex problems at the intersection of Artificial Intelligence 🤖 and Human-Computer Interaction 🖥️. My research focuses on designing intelligent, adaptive systems that enhance accessibility and usability. I'm particularly interested in machine learning, multimodal interaction, and human-centered AI solutions that positively impact people's lives 🌱.
        </p>
        <p>
          Previously, I earned my BSc in Computer Science from Habib University, Karachi, and worked as a Software Engineer for over two years, developing end-to-end applications, optimizing performance, and delivering user-focused solutions.
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "c-about",
};
</script>

<style>
.overflow-wrap {
  inline-size: 50%;
  overflow-wrap: break-word;
}
.link {
  text-decoration: none;
}
</style>