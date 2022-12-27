<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :mobile-breakpoint="768"
      app
    >
      <v-img
          class="pa-8 pt-0"
          height="40"
      >
<!--        <img :src="require(`./assets/logo.png`)" alt="">-->
      </v-img>

      <v-list
          dense
          nav
      >
        <v-list-item
            v-for="item in items"
            :key="item.title"
            :to="item.to"
            link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
        app
        shrink-on-scroll
        color="white"
        :height="$route.path === '/' ? '70' : '70'"
    >
<!--        scroll-target="#scrolling-techniques-2"-->

      <template v-slot:img="{ props }">

      </template>

      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon
              x-large
              @click="drawer=!drawer"
              color="black"
          ></v-app-bar-nav-icon>
          <v-breadcrumbs
              class="pa-4
              align-self-start
              ma-1"
              :items="breaditems"
          ></v-breadcrumbs>
          <v-spacer></v-spacer>
          <Navigation v-if="!navigation"></Navigation>
        </v-row>
      </v-container>
    </v-app-bar

    >
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

import Navigation from "@/components/Navigation";

export default {
  name: "app",
  components: {
    Navigation
  },
  data: () => ({ drawer: null,
                  navigation: null,
                  num: '',
                  items: [
                    { title: 'Text1', icon: 'mdi-food', to: '/students' },
                    { title: 'Text2', icon: 'mdi-crowd' , to: '/klasse'},
                    { title: 'Text3', icon: 'mdi-laptop' , to: '/kurse'},
                  ],
    breaditems: [
      {
        text: 'Dashboard',
        disabled: false,
        href: 'breadcrumbs_dashboard',
      },
      {
        text: 'Link 1',
        disabled: true,
        href: 'breadcrumbs_link_1',
      },
    ],
  }),

  created() {

  },
  mounted() {
  },
  computed: {

  },
  methods: {
    checkRoute() {

    },
  },
  watch: {
    $route() {
      this.checkRoute();
    }
  },

};
</script>

<style lang="scss" scoped>

</style>