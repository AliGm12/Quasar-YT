<template>
      <q-intersection transition="scale" once>
          <q-card flat class="post-card  bg-dark text-white column items-center">
            <img class="post-img" style="border-radius: 10px;" :src="cardImg" alt="">
            <q-card-section class="caption ">
              <div class="row">
                <q-avatar>
                  <img :src="avatar">
                </q-avatar>
              </div>
              <card-caption :captions="captionLists" />
            </q-card-section>
          </q-card>
          <!-- <slot name="header" :title="caption"></slot> -->
        </q-intersection>
</template>

<script>
import CardCaption from './CardCaption.vue';

  export default{
    name: 'MainCard',
    data(){
      return{
        captionLists : [this.caption, this.channelName, this.viewsAndDate]
      }
    },
    components : {
      CardCaption
    },
    props : {
      id : Number,
      cardImg : String,
      avatar : String,
      caption : String,
      channelName : String,
      viewsAndDate : String
    }
  }
</script>

<style lang="scss" scoped>
$radius-medium : 7px;
$radius-high: 20px;

.q-intersection{
  min-width: 300px;
  min-height: 300px;
}

.caption{
  align-self: flex-start;
  width: 100%;
  display: flex;
  gap: 10px;
}
.second-part{
  width: 100%;
}
</style>
