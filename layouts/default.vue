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
      <!--
      <v-app-bar-nav-icon
        v-show="$vuetify.breakpoint.smAndDown"
        @click.stop="drawer = !drawer"
      />
      <template v-if="$vuetify.breakpoint.mdAndUp">
        <v-toolbar-title style="width: 350px; line-height: 1.3em">
          <span style="font-size: 0.6em; vertical-align: top;">N-HighSchool-Railway-Club</span>
          <br>
          <span style="font-size: 1.4em;">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>
      <template v-else>
        <v-toolbar-title style="padding-left: 5px;">
          <span style="font-size: 1.4em;">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>
      -->

      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
      />

      <!-- <v-btn
        v-if="$vuetify.breakpoint.smAndDown"
        icon
        @click.stop="drawer = !drawer"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn> -->

      <template v-if="$vuetify.breakpoint.mdAndUp">
        <v-toolbar-title style="padding-left: 5px; width: 350px;">
          <span style="font-size: 1.4em;">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>
      <template v-else>
        <v-toolbar-title style="padding-left: 5px;">
          <span style="font-size: 1.4em;">N高鉄道同好会</span>
        </v-toolbar-title>
      </template>

      <v-tabs v-show="$vuetify.breakpoint.mdAndUp" class="late-show">
        <v-tab
          v-for="(item, i) in tabItems"
          :key="i"
          :to="item.to"
          style="font-family: 'Noto Sans JP', sans-serif; font-weight: 700;"
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
      <span v-if="!$device.isMobile">:Desktop</span>
      <span v-else>:Mobile</span>
      <span>:</span>
      <span>{{ $vuetify.breakpoint.name }}</span>
    </v-footer>
  </v-app>
</template>

<style scoped>
.late-show {
  /* アニメーション */
  /* animation: fadeIn 1s linear;
  animation-fill-mode: both; */
}

@keyframes fadeIn{
    0%{
        opacity: 0;
    }
    90% {
        opacity: 0;
    }
    100%{
        opacity: 1;
    }
}
</style>

<script>
// import isMobile from 'ismobilejs'
// isMobile: debugMode ? true : isMobile.any,

// PC&tabの時に出すもの： $device.isDesktopOrTablet
// Mobileの時に出すもの： $device.isMobile

// PC&tabの時に出すもの： $vuetify.breakpoint.mdAndUp
// Mobileの時に出すもの： $vuetify.breakpoint.smAndDown

export default {
  data () {
    return {
      clipped: false,
      drawer: false,
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
  },
  methods: {
    bkPint () {
      const bkPt = this.$vuetify.breakpoint
      return bkPt.name
    }
  }
}
</script>
