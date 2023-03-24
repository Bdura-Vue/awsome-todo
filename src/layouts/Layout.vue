<template>
  <q-layout view="hHh lpr fFf">
    <q-header elevated>
      <q-toolbar>
        <!-- <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" /> -->

        <q-toolbar-title class="absolute-center">
          Awesome Todo
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-footer>
      <q-tabs>

          <q-route-tab v-for="nav in navs" :to="nav.to" :icon="nav.icon" :label="nav.label" :key="nav.label" />


      </q-tabs>
    </q-footer>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered :breakpoint="767" width="200" class="bg-primary">
      <q-list >
        <q-item-label header class="text-grey-4">
          Navigation
        </q-item-label>

        <!-- Home page -->
        <q-item v-for="nav in navs" :to="nav.to" :key="nav.label" exact clickable class="text-grey-4">
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
            <!-- <q-item-label caption>quasar.dev</q-item-label> -->
          </q-item-section>
        </q-item>


      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',



  setup() {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      navs: [
        {
          label: "Todo",
          icon: "list",
          to: "/"
        },
        {
          label: "Settings",
          icon: "settings",
          to: "/settings"
        },
      ]
    }
  }
})
</script>


<style lang="scss">
  @media screen and (min-width: 767px) {
    .q-footer {
      display: none;
    }
  }

  .q-drawer {
    .q-router-link--active {
      color: white !important
    }
  } 

</style>
