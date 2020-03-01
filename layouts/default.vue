<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
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
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-icon id="apolloStatus" color="green">
        mdi-checkbox-marked-circle
      </v-icon>
      <v-tooltip attach="apolloStatus">Apollo - Healthy</v-tooltip>
      <v-icon color="green">mdi-checkbox-marked-circle</v-icon>
      <v-icon color="orange">mdi-alert</v-icon>
      <v-icon color="red">mdi-minus-circle</v-icon>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: true,
      items: [
        {
          icon: 'mdi-information-outline',
          title: 'Practice Details',
          to: '/practice'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Databases',
          to: '/inspire'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Settings',
          to: '/settings'
        }
      ],
      miniVariant: false,
      right: false,
      rightDrawer: false,
      title: 'Monocle - ' + this.$route.query.practiceId
    }
  }
}
</script>
