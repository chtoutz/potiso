<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
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
          Pot'Iso App
        </q-toolbar-title>

        <div>Pot'Iso v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
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

    <q-page-container>
      <router-view />
    </q-page-container>
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
      essentialLinks: linksData
    }
  }
}
</script>
