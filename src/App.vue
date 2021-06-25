<template>
  <v-app id="inspire">
      <v-navigation-drawer 
      v-model="drawer"
      :mobile-breakpoint="768"
      app>

<v-img
  class="pa-4 pt-5"
  height="170"
  src="https://picsum.photos/id/11/500/300"
  gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)">

  <v-avatar size="100" class="mb-2">
    <img
  src="https://scontent.flhr1-2.fna.fbcdn.net/v/t1.6435-9/141104558_10158076182801743_2657202474725968494_n.jpg?_nc_cat=110&ccb=1-3&_nc_sid=09cbfe&_nc_ohc=mbKS6-rKN5EAX96zdJS&_nc_ht=scontent.flhr1-2.fna&oh=622c0fffe7fefc4e5cc79613ea4c547c&oe=60DA1170"
  color="primary"
  size="56"
></v-avatar>
<div class="white--text text-subtitle-1 font-weight-bold">Ilja Gonciarov</div>
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
      color="primary"
      dark
      
      src="https://picsum.photos/1920/1080?random"
      height="170"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          <v-spacer></v-spacer>
          <search />
        </v-row>
         <v-row>
           <v-toolbar-title class="text-h4 ml-4"> {{ $store.state.appTitle }} </v-toolbar-title>
        </v-row>
        <v-row>
          <live-date-time />
        </v-row>
      </v-container>

      

    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snackbar />
    </v-main>
  </v-app>
</template>

<script>

  export default {
    data: () => ({ 
        drawer: null,
         items: [
          { title: 'Todo', icon: 'mdi-format-list-checks', to: '/' },
          { title: 'About', icon: 'mdi-help-box', to: '/about' },
        ]
       }),

       components: {
         'search': require('@/components/Tools/Search.vue').default,
         'live-date-time': require('@/components/Tools/LiveDateTime.vue').default,
         'snackbar': require('@/components/Shared/Snackbar.vue').default
       }
  }
</script>

<style lang="sass">
.header-container 
  max-width: none !important

</style>