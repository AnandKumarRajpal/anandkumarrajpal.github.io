<template>
  <v-container id="contact">
    <v-row class="main-container">
      <v-col class="px-0 py-0">
        <v-row class="mx-0 mb-4 my-0 align-center">
          <p class="code-style darkText section-heading my-0">03 - Contact</p>
          <v-divider class="ml-4"></v-divider>
        </v-row>
        <div class="text-center">
          <v-btn
            v-for="(icon, index) in icons"
            :key="icon"
            class="mx-6 my-4"
            icon
            :href="iconLink[index]"
            target="_blank"
          >
            <v-icon size="42px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "c-contact",
  data() {
    return {
      icons: [
        "mdi-linkedin",
        "mdi-twitter",
        "mdi-github",
        "mdi-email",
      ],
      iconLink: [
        "https://www.linkedin.com/in/anand-kumar-rajpal/",
        "https://twitter.com/rajpal_anand",
        "https://github.com/AnandKumarRajpal/",
        "mailto:anandrajpal123@gmail.com"
      ],
    };
  },
};
</script>

<style>
</style>