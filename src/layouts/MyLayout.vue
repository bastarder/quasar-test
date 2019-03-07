<template>
  <q-layout view="lHh Lpr lFf">
    <q-layout-header class="no-shadow header">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerMini = !leftDrawerMini"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <div class="nav-header">
          <a>Home</a>
          <a>About</a>
          <a>Services</a>
          <a>
            Project
            <q-icon name="expand_more" />
            <q-popover anchor="bottom left" self="top left">
              <q-list separator link>
                <q-item v-close-overlay>
                  aaaa
                </q-item>
                <q-item v-close-overlay>
                  bbbb
                </q-item>
              </q-list>
            </q-popover>
          </a>
          <a>Support</a>
        </div>

      </q-toolbar>
    </q-layout-header>

    <q-layout-drawer
      class="no-shadow"
      v-model="leftDrawerOpen"
      :mini="leftDrawerMini"
      :mini-width="80"
    >
      <img v-if="!leftDrawerMini" class="logo" src="~assets/logo.png">
      <img v-else class="logo mini" src="~assets/logosn.png">

      <q-list
        class="nav-menu"
        no-border
        link
        inset-delimiter
      >
        <q-collapsible icon="explore" label="First">
          <q-item @click.native="openURL('http://quasar-framework.org')">
            <q-item-side icon="school" />
            <q-item-main label="Docs" sublabel="quasar-framework.org" />
          </q-item>
          <q-item @click.native="openURL('http://quasar-framework.org')">
            <q-item-side icon="school" />
            <q-item-main label="Docs" sublabel="quasar-framework.org" />
          </q-item>
        </q-collapsible>
        <q-item @click.native="openURL('http://quasar-framework.org')">
          <q-item-side icon="school" />
          <q-item-main label="Docs" sublabel="quasar-framework.org" />
        </q-item>
        <q-item @click.native="openURL('https://github.com/quasarframework/')">
          <q-item-side icon="code" />
          <q-item-main label="GitHub" sublabel="github.com/quasarframework" />
        </q-item>
        <q-item @click.native="openURL('https://discord.gg/5TDhbDg')">
          <q-item-side icon="chat" />
          <q-item-main label="Discord Chat Channel" sublabel="https://discord.gg/5TDhbDg" />
        </q-item>
        <q-item @click.native="openURL('http://forum.quasar-framework.org')">
          <q-item-side icon="record_voice_over" />
          <q-item-main label="Forum" sublabel="forum.quasar-framework.org" />
        </q-item>
        <q-item @click.native="openURL('https://twitter.com/quasarframework')">
          <q-item-side icon="rss feed" />
          <q-item-main label="Twitter" sublabel="@quasarframework" />
        </q-item>
      </q-list>
    </q-layout-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'MyLayout',
  data () {
    return {
      // leftDrawerOpen: this.$q.platform.is.desktop,
      leftDrawerOpen: true,
      leftDrawerMini: false,
    }
  },
  methods: {
    openURL
  },
  computed: {
  }
}
</script>

<style lang="stylus">
  @import '~variables'

  $header-height = 80px

  .nav-header
    a
      display inline-block
      margin 0 20px
      user-select none

  .no-shadow
    .q-layout-drawer-delimiter
      box-shadow none

  .q-toolbar
    height $header-height

  .logo
    background-color white
    display inline-block
    width 100%
    height $header-height

  .mini
    padding 16px

  .q-layout-page-container
    background: #f6f8fa;
</style>


<style>
  .q-layout-drawer{
    overflow: hidden;
    width: 200px;
  }
  .nav-menu{
    height: 100vh;
    overflow-y: scroll;
  }
</style>
