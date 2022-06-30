<template>
  <v-app style="background-color: #c7ffff">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :src="image"
      fixed
      app
    >
      <v-list>
        <v-list-item>
          <v-list-item-content>
            <v-row>
              <div class="ml-3">
                <img src="../assets/img/logo.png" width="100" />
              </div>
            </v-row>
          </v-list-item-content>
        </v-list-item>
      </v-list>

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
      <template #append>
        <div class="pr-2 pt-2 pb-2">
          <v-btn
            style="background-color: transparent !important"
            @click="logout"
          >
            <v-icon light class="mr-5"> mdi-logout-variant </v-icon>
            Logout
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      light
      flat
      style="background-color: #c7ffff"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <!-- <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>mdi-minus</v-icon>
      </v-btn> -->
      <v-toolbar-title style="font-weight: 600" v-text="title" />
      <v-spacer />
      <!-- <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>mdi-application</v-icon>
      </v-btn>
      
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn> -->
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <!-- <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  layout: 'empty',
  data() {
    return {
      image: require('@/assets/img/sidebar.png'),
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-view-dashboard',
          title: 'Dashboard',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Produk',
          to: '/produk',
        },
        {
          icon: 'mdi-order-bool-descending-variant',
          title: 'Daftar Pesanan',
          to: '/pesanan',
        },
        {
          icon: 'mdi-receipt-text-check-outline',
          title: 'Invoice',
          to: '/invoice',
        },
        {
          icon: 'mdi-advertisements',
          title: 'Iklan Promo',
          to: '/iklanPromo',
        },
        {
          icon: 'mdi-wallet-plus',
          title: 'Pembayaran',
          to: '/pembayaran',
        },
      ],
      miniVariant: false,
      right: true,

      title: 'Payment Point Online Banking (PPOB) uPay',
    }
  },
  methods: {
    logout() {
      localStorage.setItem('authenticated', false)
      this.$router.push('login')
    },
    // minimizeNav() {
    //   this.drawer = !this.drawer
    //   this.miniVariant = !this.miniVariant
    // },
  },
}
</script>
<style>
html {
  font-family: 'Poppins', sans-serif;
}
</style>
