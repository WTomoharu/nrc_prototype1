<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      mdi-minus
      temporary
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon
        v-show="isMobile"
        @click.stop="drawer = !drawer"
      />
      <template v-if="!isMobile">
        <v-toolbar-title>
          <span style="font-size: 0.6em">N-HighSchool-Railway-Club</span>
          <br>
          <span style="font-size: 1.3em; line-height:0.2">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>
      <template v-else>
        <v-toolbar-title>
          N高鉄道同好会
        </v-toolbar-title>
      </template>

      <v-spacer />
      <v-btn
        icon
        href="https://twitter.com/home"
      >
        <v-icon>mdi-twitter</v-icon>
      </v-btn>
      <v-btn
        icon
        href="https://n-highschool.slack.com/archives/C5NAM13S6"
      >
        <v-icon>mdi-slack</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import isMobile from 'ismobilejs'

// 強制的にスマホモードにする
const debugMode = false

export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      isMobile: debugMode ? true : isMobile.any,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
