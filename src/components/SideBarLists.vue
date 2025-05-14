<template>
      <q-list padding class="q-gutter-md">
        <q-item
          v-show="showBtns"
          v-if="!showBtn"
          clickable
          v-ripple
          style="border-radius: 15px;"
          :class="[{'q-pl-none': miniState, 'q-pr-lg': miniState}]"
        >
          <q-item-section avatar>
            <q-icon name="fa-solid fa-house" />
          </q-item-section>
          <q-item-section class="text-subtitle1 text-weight-bold">
            صفحه اصلی
          </q-item-section>
        </q-item>
        <q-btn v-if="showBtn" unelevated flat fab-mini dense :ripple="false" label="صفحه اصلی" icon="fa-solid fa-house" />

        <q-item
          v-show="showBtns"
          v-if="!showBtn"
          clickable
          v-ripple
          style="border-radius: 15px;"
          :class="[{'q-pl-none': miniState, 'q-pr-lg': miniState}]"
        >
          <q-item-section avatar>
            <q-icon name="fa-solid fa-film" />
          </q-item-section>
          <q-item-section class="text-subtitle1 text-weight-bold">
            ویدیو های کوتاه
          </q-item-section>
        </q-item>
        <q-btn v-if="showBtn" unelevated flat fab-mini dense :ripple="false" label="ویدیو های کوتاه" icon="fa-solid fa-film" />


        <q-item
        v-show="showBtns"
          v-if="!showBtn"
          clickable
          v-ripple
          style="border-radius: 15px;"

          :class="[{'q-pl-none': miniState, 'q-pr-lg': miniState}]"
        >
          <q-item-section avatar>
            <q-icon name="fa-solid fa-thumbs-up" />
          </q-item-section>
          <q-item-section class="text-subtitle1 text-weight-bold">
            پسندیده ها
          </q-item-section>
        </q-item>
        <q-btn v-if="showBtn" unelevated flat fab-mini dense :ripple="false" label="پسندیده ها" icon="fa-solid fa-thumbs-up" />

      </q-list>
</template>

<script>
  export default {
    name : 'SideBarLists',
    props : {
      showBtn : Boolean,
      showBtns : {
        type : Boolean,
        default : '#'
      }
    },
    data(){
      return {
        miniState : false
      }
    },
    computed : {
      hideItem(){
        return this.showBtns
      }
    }
  }
</script>

<style lang="sass" scoped>

</style>
