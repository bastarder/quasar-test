<template>
  <div class="row">
    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12">
      <div class="search-bar">
        <div class="row">
          <div class="col-lg-6 col-md-6 col-sm-6 col-xs-12">
            <q-search 
              placeholder="Search..." value=""/>
          </div>
          <div class="col-lg-6 col-md-6 col-sm-6 col-xs-0 breadcrumb">
            <q-breadcrumbs>
              <q-breadcrumbs-el label="Home" />
              <q-breadcrumbs-el label="Dashboard V.1" />
            </q-breadcrumbs>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'ComponentName',
  data () {
    return {}
  }
}
</script>


<style lang="stylus" scoped>
  .search-bar
    padding 20px
    background: #fff;
    margin 20px 15px 30px 15px
    height 74px
  .q-breadcrumbs
    float right
  // .q-input
  //   width: 200px
  .breadcrumb
    overflow hidden
</style>

