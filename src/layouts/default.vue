<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">

         <v-list>
          <v-list-item
            prepend-avatar="https://img.freepik.com/fotos-premium/avatar-mulher-geek-furiosa_949597-34.jpg?w=740"
            title="Maria Silva"
            subtitle="maria@google.com"
          >
            <template v-slot:append>
              <v-btn
                size="small"
                variant="text"
                icon="mdi-menu-down"
              ></v-btn>
            </template>
          </v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list
          :lines="false"
          density="compact"
          nav
          >
          <router-link
            v-for="(item, i) in items"
            :key="i"
            :to="item.to"
            >
            <v-list-item
              :value="item"
              color="primary">
              <template v-slot:prepend>
                <v-icon :icon="item.icon"></v-icon>
              </template>

              <v-list-item-title v-text="item.text"></v-list-item-title>         
            </v-list-item>
          </router-link>
        </v-list>
    </v-navigation-drawer>

    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Application</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'

  const drawer = ref(null);

  const items = [
        { text: 'Home', icon: 'mdi-folder', to: "/" },
        { text: 'About', icon: 'mdi-account-multiple', to: "/about" },
      ];

</script>