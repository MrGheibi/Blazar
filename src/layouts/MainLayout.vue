<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="b-header b-shadow bg-white text-grey-8">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Blazar
        </q-toolbar-title>

        <q-space/>

        <div class="q-gutter-sm row items-center no-wrap">
          <q-toggle
            v-model="dark"
            checked-icon="mdi-theme-light-dark"
            :label="dark? 'شب' : 'روز'"
            color="green"
            unchecked-icon="mdi-theme-light-dark"
          />

          <q-btn round dense flat :icon="$q.fullscreen.isActive ? 'fullscreen_exit' : 'fullscreen'"
                 @click="$q.fullscreen.toggle()"
                 v-if="$q.screen.gt.sm">
            <q-tooltip>تمام صفحه</q-tooltip>
          </q-btn>
          <q-btn dense flat color="danger" icon="logout">
            <q-tooltip>خروج</q-tooltip>
          </q-btn>

        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      :width="260"
      v-model="leftDrawerOpen"
      show-if-above
      content-class="bg-grey-1"
    >
      <q-list>
        <div class="flex flex-center">
          <img
            class="shadow-3 profile-img"
            alt="Blazar logo"
            src="~assets/images/profile.jpg"
            width="160"
          >
          <span class="profile-text">
          ایلان ماسک
          </span>
        </div>

        <q-separator inset="true" class="q-my-sm"/>
        <SideBar></SideBar>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view/>
    </q-page-container>
  </q-layout>
</template>

<script>

import SideBar from 'components/SideBar'

export default {
  name: 'MainLayout',
  components: {
    SideBar
  },
  data () {
    return {
      dark: false,
      leftDrawerOpen: false
    }
  }
}
</script>
