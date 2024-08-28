<template>
  <v-app class="light-blue-background">
    <v-navigation-drawer app v-model="drawer" color="blue darken-3" dark>
      <v-list dense>
        <v-list-item-group>
          <v-list-item v-for="(item, index) in items" :key="index" @click="navigate(item.route)">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="blue darken-2" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="headline">
        Welcome
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text href="#">
        <v-icon left>mdi-home</v-icon>
        หน้าแรก
      </v-btn>
      <v-btn text href="#">
        <v-icon left>mdi-information-outline</v-icon>
        เกี่ยวกับ
      </v-btn>
    </v-app-bar>

    <v-main>
      <NuxtPage></NuxtPage>
    </v-main>

    <v-footer app color="blue darken-2" dark>
      <v-col class="text-center">
        &copy; {{ new Date().getFullYear() }} Your Company Name
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      items: [
        { title: 'หน้าแรก', icon: 'mdi-home', route: '/' },
        { title: 'เกี่ยวกับ', icon: 'mdi-information-outline', route: '/about' },
      ],
    };
  },
  methods: {
    navigate(route) {
      this.$router.push(route);
    },
  },
};
</script>

<style scoped>
.light-blue-background {
  background-color: #e3f2fd; /* สีฟ้าอ่อน */
  min-height: 100vh; /* ให้ครอบคลุมทั้งหน้าจอ */
}

.headline {
  font-weight: bold;
  font-size: 24px;
}

.v-btn {
  margin-left: 16px;
  margin-right: 16px;
}
</style>
