<template>
  <q-layout class="custom-class" view="hHh LpR LFf">
    <q-header class="q-py-sm" elevated  style="background-color: #121212;">
      <q-toolbar>
        <q-header-custom @hideSidebar="miniState = true; showBtns=false; showBtnFunc()" />
        <q-toolbar-title class="row items-center ">
          YouTube
          <q-icon  class="text-h4 text-red-14 q-pr-sm" name="fa-brands fa-youtube" />
        </q-toolbar-title>
        <q-space />
        <div style="flex-wrap: nowrap;" class="row items-center">
          <q-input dense hide-bottom-space debounce  label-color="yellow" color="yellow" class="header-input q-px-md" v-model="text" label="جستجو" />
          <q-btn size="16px" class="search-btn"  icon="search"/>
        </div>
        <q-btn class="q-mr-md bg-purple q-px-sm"  rounded icon="fa-solid fa-microphone" >
          <q-tooltip class="text-subtitle1">
          جستجو با صدای خودتان
        </q-tooltip>
        </q-btn>
        <q-space />
        <div class="row items-center q-pl-md q-gutter-md">
          <q-btn class="row items-center justify-center q-pl-sm bg-purple" rounded dense label="ایجادکردن" icon="add" />
          <q-btn class="q-py-sm q-px-sm" dense rounded icon="fa-regular fa-bell" >
            <q-badge color="red" rounded floating>4</q-badge>
          </q-btn>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar.png">
          </q-avatar>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
    :bordered="false"
    side="right"
    v-model="drawer"
    show-if-above
    :mini="!drawer || miniState"
    @click.capture="drawerClick($event);hideBtnFunc()"
    :width="miniState ? 56 : 230"
    :breakpoint="700"
    :mini-width="107"
    :class="[$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3']"
  >
    <q-scroll-area class="fit q-px-md" style="background-color: #121212;color: #fff;" :horizontal-thumb-style="{ opacity: 0 }">
      <side-bar-lists :show-btn="showBtn"/>
      <side-bar-lists :show-btns="showBtns"/>
      <side-bar-lists :show-btns="showBtns"/>

    </q-scroll-area>
  </q-drawer>



    <q-page-container>
      <router-view />
      <q-page-sticky  class="bg-dark"  expand position="top">
        <q-scroll-area ref="scrollAreaRef" visible="true" style="width: 100%;height: 63px;">
          <q-toolbar class="row text-no-wrap text-white q-px-xl q-gutter-md q-py-md">
            <q-btn class="bg-yellow" label="همه" size="12px" />
            <q-btn class="bg-purple" label="موسیقی" size="12px" />
            <q-btn class="bg-purple" label="بازی" size="12px" />
            <q-btn class="bg-purple" label="زنده" size="12px" />
            <q-btn class="bg-purple" label="گلچین‌ها" size="12px" />
            <q-btn class="bg-purple" label="فوتبال" size="12px" />
            <q-btn class="bg-purple" label="بازی‌های ماجراجویی اکشن" size="12px" />
            <q-btn class="bg-purple" label="رپ‌خوانی" size="12px" />
            <q-btn class="bg-purple" label="اخیرا بارگذاری شده" size="12px" />
            <q-btn class="bg-purple" label="تماشاشده" size="12px" />
            <q-btn class="bg-purple" label="جدید برای شما" size="12px" />
          </q-toolbar>
        </q-scroll-area>
        <q-btn v-if="windowWidth <= 1200 ? true : false" @click="scrollLeft" size="10px" class="left-slide " icon="fa-solid fa-angle-left" :round="true" color="black"/>
        <q-btn v-if="windowWidth <= 1200 ? true : false" @click="scrollRight" size="10px" class="right-slide " icon="fa-solid fa-angle-right" :round="true" color="black"/>
      </q-page-sticky>
    </q-page-container>

  </q-layout>
</template>

<script>
import { matMenu } from '@quasar/extras/material-icons'
import { mdiAbTesting } from '@quasar/extras/mdi-v7'
import { fasFont } from '@quasar/extras/fontawesome-v5'
import SideBarLists from 'src/components/SideBarLists.vue'
import QHeaderCustom from 'src/components/QHeaderCustom.vue'

const linksList = [
  {
    title: 'سلام',
    caption: 'سلام سشلام',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default {
  name: 'MainLayout',

  components: {
    QHeaderCustom,
    SideBarLists
  },

  data () {
    return {
      showBtn : false,
      showBtns : true,
      showBtnTimeout : null,
      linksList,
      drawer:false,
      miniState : false,
      matMenu,
      mdiAbTesting,
      fasFont,
      text : '',
      leftScroll : 0,
      rightScroll : 0,
      windowWidth : 0
    }
  },
  mounted(){
    this.windowWidth = window.innerWidth;

    // Add resize event listener
    window.addEventListener('resize', this.updateWindowWidth)
  },
  methods: {
    drawerClick (e) {

        // if in "mini" state and user
        // click on drawer, we switch it to "normal" mode
        if (this.miniState) {
          this.miniState = false

          // notice we have registered an event with capture flag;
          // we need to stop further propagation as this click is
          // intended for switching drawer to "normal" mode only
          e.stopPropagation()
        }
      },
      showBtnFunc () {
        this.showBtnTimeout =  setTimeout(()=>{
          this.showBtn = true
        },200)
      },
      hideBtnFunc () {
        clearTimeout(this.showBtnFunc)
        this.showBtn = false
        this.showBtns = true
      },
      scrollLeft(){
        console.log(this.$refs.scrollAreaRef.getScrollPercentage());

        this.leftScroll = this.$refs.scrollAreaRef.getScrollPercentage().left + 0.3
        this.$refs.scrollAreaRef.setScrollPercentage('horizontal', -this.leftScroll, 300)
      },
      scrollRight(){
        this.rightScroll = this.$refs.scrollAreaRef.getScrollPercentage().left - 0.3
        this.$refs.scrollAreaRef.setScrollPercentage('horizontal', -this.rightScroll, 300)
      },
      updateWindowWidth(){
        this.windowWidth = window.innerWidth
      }
  }
}
</script>

<style lang="scss" scoped>
$primary-color: #555;
$radius-medium : 7px;
$radius-high: 20px;
$gray-btn : #6b6b6b;
$zero : 0px;

.active{
  background: $primary-color;
}

.header-input{
  width: 500px;
  border-top-right-radius: $radius-high;
  border-bottom-right-radius: $radius-high;
  border-top-left-radius: $zero;
  border-bottom-left-radius: $zero;
  border-right: 1px solid #555;
  border-top: 1px solid #555;
  border-bottom: 1px solid #555;
}
@media (max-width:1200px) {
  .header-input{
    max-width: 300px;
  }
}
.search-btn{
  background: $purple;
  border-top-left-radius: $radius-high;
  border-bottom-left-radius: $radius-high;
  border-top-right-radius: $zero;
  border-bottom-right-radius: $zero;
  border: 1px solid $gray-btn;
}
.q-page-sticky{
  display: flex;
  align-items: center;
}
.q-page-sticky .q-btn{
  border-radius: $radius-medium;
}
.q-page-sticky .left-slide{
  position: absolute;
  left: 10%;
  border-radius: 100%;
}
.q-page-sticky .right-slide{
  position: absolute;
  right: 10%;
  border-radius: 100%;
}
</style>

