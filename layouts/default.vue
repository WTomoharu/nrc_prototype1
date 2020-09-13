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
          v-for="(item, i) in tabItems"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.titleJa" />
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
        <v-toolbar-title style="width: 350px; line-height: 1.3em">
          <span style="font-size: 0.6em; vertical-align: top;">N-HighSchool-Railway-Club</span>
          <br>
          <span style="font-size: 1.4em;">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>
      <template v-else>
        <v-toolbar-title>
          <span style="font-size: 1.4em;">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>

      <v-tabs v-if="!isMobile">
        <v-tab
          v-for="(item, i) in tabItems"
          :key="i"
        >
          {{ item.titleJa }}
        </v-tab>
      </v-tabs>

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
      <!-- <v-container style="height: 1000px;"></v-container> -->
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
      tabItems: [
        {
          icon: 'mdi-apps',
          titleJa: 'ホーム',
          titleEn: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          titleJa: '当会について',
          titleEn: 'About',
          to: '/about'
        },
        {
          icon: 'mdi-chart-bubble',
          titleJa: 'よくある質問',
          titleEn: 'F&Q',
          to: '/faq'
        },
        {
          icon: 'mdi-chart-bubble',
          titleJa: 'ブログ',
          titleEn: 'Blog',
          to: '/blog'
        },
        {
          icon: 'mdi-chart-bubble',
          titleJa: 'リンク集',
          titleEn: 'Links',
          to: '/links'
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
