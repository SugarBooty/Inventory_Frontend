<template>
  <nav>
    <v-app-bar app color="primary" dark dense shaped clipped-left>
      <v-app-bar-nav-icon @click="invertDrawer"></v-app-bar-nav-icon>

      <!-- <v-icon large class="mr-3">mdi-clipboard-text-multiple-outline</v-icon> -->
      Inventory System
    </v-app-bar>
    <!-- <v-navigation-drawer
    app
    dark
    permanent
    expand-on-hover
    v-model="drawer"
    color="primary"
    style="top: 48px">
      <v-list>
            <v-list-item class="px-2">
              <v-list-item-avatar>
                <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img>
              </v-list-item-avatar>
            </v-list-item>

            <v-list-item link>
              <v-list-item-content>
                <v-list-item-title class="title">Dan</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>

          <v-divider></v-divider>

          <v-list
            nav
            dense
          >
            <v-list-item link>
              <v-list-item-icon>
                <v-icon>mdi-folder</v-icon>
              </v-list-item-icon>
              <v-list-item-title>My Files</v-list-item-title>
            </v-list-item>
            <v-list-item link>
              <v-list-item-icon>
                <v-icon>mdi-account-multiple</v-icon>
              </v-list-item-icon>
              <v-list-item-title>Shared with me</v-list-item-title>
            </v-list-item>
            <v-list-item link>
              <v-list-item-icon>
                <v-icon>mdi-star</v-icon>
              </v-list-item-icon>
              <v-list-item-title>Starred</v-list-item-title>
            </v-list-item>
          </v-list>
    </v-navigation-drawer> -->

    <v-navigation-drawer
      v-model="drawer"
      color="primary"
      style="0px"
      clipped
      app
      dark
    >
      <v-list shaped>
        <v-list-item class="px-2">
          <v-list-item-avatar>
            <v-img
              src="https://randomuser.me/api/portraits/women/75.jpg"
            ></v-img>
          </v-list-item-avatar>

          <v-list-item-title wrap>
            Daniel Frivolopolous
          </v-list-item-title>
          <v-btn
            icon
            exact
            router
            to="/settings"
          >
            <v-icon>mdi-cog</v-icon>
          </v-btn>
        </v-list-item>

        <v-divider></v-divider>

        <v-list-item-group v-model="item" color="white">
          <v-list-item
            v-for="item in items"
            :key="item.text"
            router
            :to="item.route"
          >
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
      item: 0,
      items: [
        { text: "Home", icon: "mdi-home", route: "/" },
        { text: "My Carts", icon: "mdi-cart", route: "/carts" },
      ],
    };
  },
  methods: {
    invertDrawer() {
      this.drawer = !this.drawer;
      console.log(this.drawer);
    },
  },
};
</script>
