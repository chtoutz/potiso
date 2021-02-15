<template>
  <q-layout view="hHh lpR fff">
    <q-header reveal elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar class="bg-light-green">
        <q-btn dense flat round icon="menu" aria-label="Left menu" @click="leftDrawerOpen = !leftDrawerOpen" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          Pot'Iso
        </q-toolbar-title>

        <q-btn flat round dense icon="account_circle" class="q-mr-xs" />

        <q-btn dense flat round icon="menu" aria-label="Right menu" @click="rightDrawerOpen = !rightDrawerOpen" />
      </q-toolbar>

      <q-tabs align="left" class="bg-light-green-5">
        <q-route-tab to="/potager" label="Potager" />
        <q-route-tab to="/outilage" label="Outillage" />
        <q-route-tab to="/accessoires" label="Accessoires" />
        <q-route-tab to="/grainotheque" label="Grainothèque" />
      </q-tabs>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered content-class="bg-grey-1">
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Essential Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-7 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <!-- <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar> -->
          Footer
        </q-toolbar-title>
        Quasar v{{ $q.version }}
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Docs',
    caption: 'potiso.dev',
    icon: 'school',
    link: 'https://potiso.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/potisoframework',
    icon: 'code',
    link: 'https://github.com/potisoframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.potiso.dev',
    icon: 'chat',
    link: 'https://chat.potiso.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.potiso.dev',
    icon: 'record_voice_over',
    link: 'https://forum.potiso.dev'
  },
  {
    title: 'Twitter',
    caption: '@potisoframework',
    icon: 'rss_feed',
    link: 'https://twitter.potiso.dev'
  },
  {
    title: 'Facebook',
    caption: '@Pot\'IsoFramework',
    icon: 'public',
    link: 'https://facebook.potiso.dev'
  },
  {
    title: 'Pot\'Iso Awesome',
    caption: 'Community Pot\'Iso projects',
    icon: 'favorite',
    link: 'https://awesome.potiso.dev'
  }
]

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      rightDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
