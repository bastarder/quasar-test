<template>
  <div>
    <img v-if="!leftDrawerMini" class="logo" src="~assets/logo.png">
    <img v-else class="logo mini" src="~assets/logosn.png">

    <q-scroll-area
      :style="{
        width: scrollAreaWidth,
        height: '100vh',
      }"
      :thumb-style="{
        right: '4px',
        borderRadius: '2px',
        background: '#006df0',
        width: '4px',
        opacity: 1
      }"
    >
      <q-list class="nav-side" no-border link>
        <div v-for="item in menuData" :key="item.title">
          <q-item v-if="!item.child">
            <q-item-side :icon="item.icon" />
            <q-item-main :label="item.title"/>
          </q-item>
          <div v-else>
            <div>
              <q-popover v-model="miniStatus[item.title]" anchor="top right" self="top left" >
                <div v-for="subItem in item.child" :key="subItem.title">
                  {{ subItem.title }}
                </div>
              </q-popover>
            </div>
            <q-collapsible :icon="item.icon" :label="item.title" collapse-icon="expand_more">
              <q-item v-for="subItem in item.child" :key="subItem.title">
                <q-item-main :label="subItem.title"/>
              </q-item>
            </q-collapsible>
          </div>
        </div>
      </q-list>
    </q-scroll-area>
  </div>
</template>

<script>
export default {
  props: ['leftDrawerMini'],
  data () {
    return {
      miniStatus: {
        eduaction: false,
        professor: false,
      },
      count: {
        eduaction: 0,
        professor: 0,
      },
      menuData: [
        {
          icon: 'explore',
          title: 'Eduaction',
          child: [
            { title: 'Dashboard v.1' },
            { title: 'Dashboard v.2' },
            { title: 'Dashboard v.3' },
            { title: 'Analytics' },
            { title: 'widgets' },
          ],
        },
        {
          icon: 'explore',
          title: 'Event',
        },
        {
          icon: 'explore',
          title: 'Professor',
          child: [
            { title: 'All Professors' },
            { title: 'Add Professor' },
            { title: 'Edit Professor' },
            { title: 'Professor Profile' },
          ],
        },
      ]
    }
  },
  computed: {
    scrollAreaWidth: function() {
      return this.leftDrawerMini ? '80px' : '200px';
    }
  },
  methods: {
    openList: function(key) {
      this.count[key]++;
      if(this.count[key] % 2 === 0){
        return;
      }
      for (const _key in this.miniStatus) {
        if(!this.leftDrawerMini){
          this.miniStatus[_key] = false;
          continue;
        }
        this.miniStatus[_key] = _key === key;
      }
    }
  }
}
</script>

<style lang="stylus">
  .nav-side
    color #8d9498
    font-size 16px
    .q-list
      padding 0
    .q-item
      user-select none
      padding 13px 15px
    .q-item:hover
      cursor auto
      background #f6f6f6
    .q-collapsible-sub-item
      padding 8px 0
      .q-item-main
        padding-left 30px
</style>
