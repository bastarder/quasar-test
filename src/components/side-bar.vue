<template>
  <div>
    <img v-if="!leftDrawerMini" class="logo" src="~assets/logo.png">
    <img v-else class="logo mini" src="~assets/logosn.png">

    <q-scroll-area
      :style="{
        width: leftDrawerMini ? '80px' : '200px',
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
      <q-list
        class="nav-side"
        no-border
        link
      >
        <div>
          <div>
            <q-popover
              v-model="miniStatus.eduaction"
              anchor="top right"
              self="top left"
              >
              <div>12312312312</div>
              <div>12312312312</div>
              <div>12312312312</div>
              <div>12312312312</div>
              <div>12312312312</div>
            </q-popover>
          </div>
          <q-collapsible icon="explore" label="Eduaction" collapse-icon="expand_more" @click.native="openList('eduaction')">
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Dashboard v.1"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Dashboard v.2"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Dashboard v.3"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Analytics"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="widgets"/>
            </q-item>
          </q-collapsible>
        </div>


        <q-item @click.native="openURL('http://quasar-framework.org')">
          <q-item-side icon="school" />
          <q-item-main label="Event"/>
        </q-item>

        <div>
          <q-collapsible icon="explore" label="Professor" collapse-icon="expand_more" @click.native="openList('professor')">
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="All Professors"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Add Professor"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Edit Professor"/>
            </q-item>
            <q-item @click.native="openURL('http://quasar-framework.org')">
              <q-item-main label="Professor Profile"/>
            </q-item>
          </q-collapsible>

          <div>
            <q-popover
              v-model="miniStatus.professor"
              anchor="top right"
              self="top left"
              >
              <div>12312312312</div>
              <div>12312312312</div>
              <div>12312312312</div>
              <div>12312312312</div>
              <div>12312312312</div>
            </q-popover>
          </div>

        </div>


      </q-list>
    </q-scroll-area>
  </div>
</template>

<script>
import { openURL } from 'quasar'

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
    }
  },
  methods: {
    openURL,
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
        this.miniStatus[_key] = _key === key
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
