<template>
  <v-app dark class="c-bg">
    <!-- PageLoader -->
    <transition name="custom-fade" mode="out-in">
      <c-page-loader v-if="isLoading"></c-page-loader>
    </transition>
    <!-- PageLoader end -->

    <div
      class="d-flex justify-center w-100 h-100 bg bg-top"
      :style="{ backgroundImage: 'url(' + require('@/assets/bg.png') + ')' }"
    ></div>

    <div
      class="d-flex justify-center w-100 h-100 bg align-end justify-center"
      style="overflow: hidden"
    >
      <img src="@/assets/bg.png" class="bg-bottom" />
    </div>

    <!-- Navbar -->
    <v-app-bar
      app
      id="appBarMain"
      class="navbar-bg"
      style="backdrop-filter: blur(6px)"
    >
      <v-container>
        <v-row class="mx-0 my-0">
          <div class="d-flex align-center my-2">
            <a href="#">
              <svg
                id="my-svg"
                viewBox="0 0 92 101"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M50.1263 6.95198L93.3263 103H71.8703L55.7423 67.72H55.8863L47.9663 50.152L40.0463 67.72L49.2623 87.88H30.9743L30.6863 88.6L24.0623 103H2.60626L45.8063 6.95198L47.8223 2.19998L50.1263 6.95198Z"
                  :stroke="this.$vuetify.theme.dark ? 'white' : 'black'"
                  stroke-width="5"
                  stroke-linejoin="round"
                />
              </svg>
            </a>
          </div>

          <v-spacer></v-spacer>

          <div class="d-none d-md-flex align-center">
            <v-btn href="#about" text>
              <span><i class="fa-solid fa-user"></i></span>
              <span class="ml-2">About</span>
            </v-btn>

            <div class="text-center">
              <v-menu open-on-hover offset-y>
                <template v-slot:activator="{ on, attrs }">
                  <v-btn href="#portfolio" text v-bind="attrs" v-on="on">
                    <span><i class="fa-solid fa-folder-closed"></i></span>
                    <span class="ml-2">Portfolio</span>
                  </v-btn>
                </template>

                <v-list class="darkLight">
                  <v-list-item
                    v-for="(item, index) in portfolioMenu"
                    :key="index"
                  >
                    <v-btn :href="item.link" text v-bind="attrs" v-on="on">
                      <span
                        ><i class="fa-solid" :class="'fa-' + item.icon"></i
                      ></span>
                      <span class="ml-2">{{ item.title }}</span>
                    </v-btn>
                  </v-list-item>
                </v-list>
              </v-menu>
            </div>

            <v-btn href="#contact" text>
              <span><i class="fa-solid fa-phone"></i></span>
              <span class="ml-2">Contact</span>
            </v-btn>

            <v-btn icon @click="toggleDarkMode()">
              <transition name="slide-fade" mode="out-in">
                <span v-if="darkMode" key="1"
                  ><i class="fa-solid fa-xl fa-sun"></i
                ></span>
                <span v-else key="2"
                  ><i class="fa-solid fa-xl fa-moon"></i
                ></span>
              </transition>
            </v-btn>
          </div>

          <v-app-bar-nav-icon
            class="d-flex d-sm-flex d-md-none"
            @click="drawer = !drawer"
          ></v-app-bar-nav-icon>
        </v-row>
      </v-container>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      fixed
      bottom
      temporary
      class="darkLight"
    >
      <v-list nav>
        <v-list-item-group v-model="activeItem">
          <v-list-item href="#about" @click="toggleDrawer()">
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>About</v-list-item-title>
          </v-list-item>

          <v-list-item
            v-for="(item, index) in portfolioMenu"
            :key="index"
            :href="item.link"
            @click="toggleDrawer()"
          >
            <v-list-item-icon>
              <v-icon v-text="item.mobIcon"></v-icon>
            </v-list-item-icon>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item>

          <v-list-item href="#contact" @click="toggleDrawer()">
            <v-list-item-icon>
              <v-icon>mdi-phone</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Contact</v-list-item-title>
          </v-list-item>

          <v-list-item href="/AnandKumar-Resume.pdf" target="_blank">
            <v-list-item-icon>
              <v-icon>mdi-file</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Resume</v-list-item-title>
          </v-list-item>

          <v-list-item @click="toggleDarkMode()">
            <v-list-item-icon>
              <transition name="slide-fade" mode="out-in">
                <span v-if="darkMode" key="1"
                  ><i class="fa-solid fa-xl fa-sun"></i
                ></span>
                <span v-else key="2"
                  ><i class="fa-solid fa-xl fa-moon"></i
                ></span>
              </transition>
            </v-list-item-icon>
            <v-list-item-title
              >Switch to {{ themeOpposite }} mode</v-list-item-title
            >
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <!-- Navbar end -->

    <v-main>
      <HelloWorld data-aos="fade-up-right" />
      <c-about data-aos="fade-up-left" data-aos-offset="250"></c-about>
      <c-work-experience
        data-aos="fade-up-right"
        data-aos-offset="250"
      ></c-work-experience>
      <c-education data-aos="fade-up-left" data-aos-offset="250"></c-education>
      <c-projects data-aos="fade-up-right" data-aos-offset="250"></c-projects>
      <c-achievements
        data-aos="fade-up-left"
        data-aos-offset="250"
      ></c-achievements>
      <c-community-projects
        data-aos="fade-up-right"
        data-aos-offset="250"
      ></c-community-projects>
      <c-contact data-aos="fade-up-left" data-aos-offset="250"></c-contact>
      <c-footer></c-footer>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import About from "./components/About.vue";
import WorkExperience from "./components/WorkExperience.vue";
import Projects from "./components/Projects.vue";
import Achievements from "./components/Achievements.vue";
import Education from "./components/Education.vue";
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";
import PageLoader from "./components/PageLoader.vue";
import CommunityProjects from "./components/CommunityProjects.vue";
import { mapGetters } from "vuex";

export default {
  name: "App",

  mounted() {
    this.$vuetify.theme.dark = true;
  },

  components: {
    HelloWorld,
    cAbout: About,
    cWorkExperience: WorkExperience,
    cProjects: Projects,
    cAchievements: Achievements,
    cEducation: Education,
    cContact: Contact,
    cFooter: Footer,
    cPageLoader: PageLoader,
    cCommunityProjects: CommunityProjects,
  },

  data: () => ({
    drawer: false,
    vivus: null,
    portfolioMenu: [
      {
        link: "#portfolio",
        title: "Work Experience",
        icon: "briefcase",
        mobIcon: "mdi-briefcase",
      },
      {
        link: "#education",
        title: "Education",
        icon: "graduation-cap",
        mobIcon: "mdi-school",
      },
      {
        link: "#projects",
        title: "Projects",
        icon: "gears",
        mobIcon: "mdi-cogs",
      },
      {
        link: "#achievements",
        title: "Achievements",
        icon: "trophy",
        mobIcon: "mdi-trophy",
      },
      {
        link: "#community-projects",
        title: "Community Projects",
        icon: "seedling",
        mobIcon: "mdi-sprout",
      },
    ],
    on: null,
    attrs: null,
    activeItem: null,
  }),

  computed: {
    darkMode() {
      return this.$vuetify.theme.dark;
    },
    theme() {
      return this.$vuetify.theme.dark ? "dark" : "light";
    },
    themeOpposite() {
      return this.$vuetify.theme.dark ? "light" : "dark";
    },
    ...mapGetters({
      isLoading: "isLoading",
    }),
  },

  methods: {
    toggleDarkMode() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
      this.drawer = false;
    },
    toggleDrawer() {
      this.drawer = !this.drawer;
    },
  },
};
</script>

<style>
#my-svg {
  overflow: visible;
  width: 30px;
}
.head-containter {
  max-width: 80%;
}

#appBarMain .v-toolbar__content {
  padding: 0 !important;
}

:root {
  --font-sans: "Manrope", "Calibre", "Inter", "San Francisco", "SF Pro Text",
    -apple-system, system-ui, sans-serif;
  --font-mono: "SF Mono", "Fira Code", "Fira Mono", "Roboto Mono", monospace;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

.custom-fade-leave-active {
  transition: all 0.5s cubic-bezier(1, 0.5, 0.8, 1);
}
.custom-fade-enter, .custom-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateY(-50px);
  opacity: 0;
}
body {
  overflow-x: hidden;
  background-color: #101820;
}
.aos-init:not(.aos-animate):after {
  position: fixed;
}
.theme--dark.c-bg {
  background-color: #111827 !important;
  /* background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100%25' height='100%25' viewBox='0 0 1600 800'%3E%3Cg stroke='%232F3A3D' stroke-width='66.7' stroke-opacity='0.2' %3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1800'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1700'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1600'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1500'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1400'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1300'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1200'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1100'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='1000'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='900'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='800'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='700'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='600'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='500'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='400'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='300'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='200'/%3E%3Ccircle fill='%23101820' cx='0' cy='0' r='100'/%3E%3C/g%3E%3C/svg%3E") !important; */
}
.theme--light.c-bg {
  background-color: #f5f5f5 !important;
  /* background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100%25' height='100%25' viewBox='0 0 1600 800'%3E%3Cg stroke='%23101820' stroke-width='66.7' stroke-opacity='0.03' %3E%3Ccircle fill='%23FFFFFF' cx='0' cy='0' r='1800'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1700'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1600'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1500'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1400'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1300'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1200'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1100'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='1000'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='900'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='800'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='700'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='600'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='500'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='400'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='300'/%3E%3Ccircle fill='%23ffffff' cx='0' cy='0' r='200'/%3E%3Ccircle fill='%23FFFFFF' cx='0' cy='0' r='100'/%3E%3C/g%3E%3C/svg%3E") !important; */
}
.c-bg {
  background-attachment: fixed !important;
  background-size: cover !important;
}

.theme--dark .darkText {
  color: #2dd4bf;
}

.theme--light .darkText {
  color: #14b8a5;
}

.section-heading {
  font-weight: bold;
}

.gradient-border-color::before {
  content: "";
  position: absolute;
  background: linear-gradient(
    to right,
    rgb(0, 220, 130),
    rgb(54, 228, 218),
    rgb(22, 167, 158)
  ) !important;
  inset: -3px;
  z-index: -1;
  opacity: 1 !important;
}

.theme--dark .navbar-bg {
  background-color: #11182780 !important;
}

.theme--light .navbar-bg {
  background-color: #ffffff80 !important;
}

.theme--light.v-sheet {
  color: rgba(0, 0, 0, 0.8);
}

.theme--light.v-application {
  color: rgba(0, 0, 0, 0.8);
}

.v-application {
  font-family: var(--font-sans) !important;
}

@media (min-width: 1904px) {
  .container {
    max-width: 1085px;
  }
}

@media (min-width: 1264px) {
  .container {
    max-width: 1085px;
  }
}

.w-100 {
  width: 100%;
}

.h-100 {
  height: 100%;
}

.bg {
  position: absolute;
  background-size: auto;
}

.bg-top {
  background-position: top;
  transform: translateY(-18rem);
}

.bg-bottom {
  transform: translateY(18rem);
}

*,
html {
  scroll-behavior: smooth !important;
}
</style>
