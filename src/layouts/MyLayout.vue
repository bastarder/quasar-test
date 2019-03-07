<template>
  <q-layout view="lHh Lpr lFf">
    <q-window-resize-observable @resize="onResize" />
    <q-layout-header class="no-shadow header">
      <q-toolbar>
        <div class="col-lg-1 col-md-0 col-sm-1 col-xs-12">
          <q-btn
            flat
            dense
            @click="toggleBar()"
            aria-label="Menu"
          >
            <q-icon name="menu" />
          </q-btn>
        </div>

        <div class="nav-header col-lg-6 col-md-7 col-sm-6 col-xs-12" >
          <a>Home</a>
          <a>About</a>
          <a>Services</a>
          <a>
            Project
            <q-icon name="expand_more" />
            <q-popover anchor="bottom left" self="top left">
              <q-list class="nav-list" link no-border>
                <q-item v-close-overlay>
                  Documentation
                </q-item>
                <q-item v-close-overlay>
                  Expert Backend
                </q-item>
                <q-item v-close-overlay>
                  Expert FrontEnd
                </q-item>
                <q-item v-close-overlay>
                  Contact Support
                </q-item>
              </q-list>
            </q-popover>
          </a>
          <a>Support</a>
        </div>

        <div class="col-lg-5 col-md-5 col-sm-12 col-xs-12">
          <div class="nav-header-right">
            <q-btn 
              class="dot"
              flat
              dense
              icon="menu"
            />

            <q-btn 
              class="dot"
              flat
              dense
              icon="menu"
            />

            <q-btn 
              class="dot"
              flat
              dense
              icon="menu"
            />

          </div>
        </div>

      </q-toolbar>
    </q-layout-header>

    <q-layout-drawer
      side="left"
      class="no-shadow"
      v-model="leftDrawerOpen"
      :mini="leftDrawerMini"
      :mini-width="80"
      :width="200"
    >
      <sider-bar :leftDrawerMini="leftDrawerMini"></sider-bar>
    </q-layout-drawer>

    <q-page-container>
      <search-bar />
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import siderbar from '../components/side-bar.vue'
import searchbar from '../components/search-bar.vue'

export default {
  components: {
    'sider-bar': siderbar,
    'search-bar': searchbar,
  },
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      leftDrawerMini: false,
      width: 0,
    }
  },
  methods: {
    toggleBar : function() {
      console.log(this.$q.platform.is.desktop)
      if(this.width <= 992){
        this.leftDrawerOpen = !this.leftDrawerOpen;
      }else{
        this.leftDrawerMini = !this.leftDrawerMini
      }
    },
    onResize : function({width}) {
      console.log(width)
      this.width = width;
      if(width > 992){
        setTimeout(() => this.leftDrawerOpen = true, 1000);
      }
    }
  },
  computed: {
  }
}
</script>

<style lang="stylus">
  @import '~variables'

  $header-height = 60px
  .nav-header-right
    float right
  .nav-header
    a
      display inline-block
      padding 20px
      font-size 14px
      user-select none
      font-weight bold

  .dot:before
    content ''
    display inline-block
    width 5px
    height 5px
    border-radius 50%
    background white
    position absolute
    top 0
    right 0

  .no-shadow
    .q-layout-drawer-delimiter
      box-shadow none

  .q-toolbar
    height $header-height
    padding 0 15px
    line-height 20px
    background #006df0 !important

  .logo
    background-color white
    display inline-block
    width 100%
    height $header-height

  .mini
    padding 16px

  .nav-list
    .q-item:hover
      background #f6f8fa
    .q-item
      color #303030
      font-size 14px

</style>


<style>
  body{
    height: 100%;
    font-family: roboto,sans-serif;
    font-weight: 400;
    background: #f6f8fa;
  }

  .q-layout-drawer{
    overflow: hidden;
  }

</style>


