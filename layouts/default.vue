<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      dark
    >
      <v-list>
        <v-list-item>
            <v-list-item-content>
            <div class="text-center">
              <img
                src="~/assets/img/account.png"
                width="80"
              />
            </div>

            <v-list-item-title class="title text-center">
              <span class="font-weight-bold text-center Hedaer-Gold">ราคาทองวันนี้</span>
            </v-list-item-title>
            <v-list-item-subtitle class="text-center">ราคาทอง ราคาหุ้น ราคาน้ำมัน</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
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
      flat
      dense
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"  />

      <v-spacer />
      <v-toolbar-title v-text="title" class="pa-2 text-h6 mycolor_header" />
      <v-spacer />
 
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; ราคาทอง ราคาทองวันนี้ เช็คราคาทอง วันนี้</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'ราคาทองคำ',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'บทความ',
          to: '/blog'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'ราคาหุ้น',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'ราคาทองวันนี้ - ChinChin.com'
    }
  }
}
</script>
