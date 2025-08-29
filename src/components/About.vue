<template>
  <v-container id="about">
    <v-row class="main-container align-center justify-center">
      <v-col class="px-0 py-0">
        <v-row class="mx-0 mb-4 my-0 align-center">
          <p class="code-style darkText section-heading my-0">01 - About Me</p>
          <v-divider class="ml-4"></v-divider>
        </v-row>

        <p>
          Hi! 👋 I'm Anand Kumar, an MSc. Computer Science (Thesis) student at the University of Calgary, supervised by Aditya Shekhar Nittala. I'm passionate about solving complex problems and exploring innovative technologies at the intersection of Artificial Intelligence 🤖 and Human-Computer Interaction 🖥️.
        </p>
        <p>
          My research focuses on designing intelligent and adaptive systems that enhance accessibility and usability. I'm particularly interested in machine learning, multimodal interaction techniques, and creating human-centered AI solutions that positively impact people's lives 🌱.
        </p>
        <p>
          Previously, I completed my BSc in Computer Science at Habib University, Karachi, and worked as a Software Engineer for 2+ years, where I developed end-to-end applications, optimized performance, and delivered user-focused solutions.
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