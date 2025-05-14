<template>
  <q-page class="main q-pl-md q-pr-md bg-dark">
    <div class="q-intersection-container">
      <main-card  v-for="(card, index) in cards" v-bind="card" :key="index" >
        <!-- <template v-slot:header="{ title }">
          <h6 class="text-white text-subtitle1"> الان من دارم از کامپوننت {{ title  }} میگیرم</h6>
        </template> -->
      </main-card>
    </div>
  </q-page>
</template>

<script>
import MainCard from 'src/components/MainPage/MainCard.vue';

export default{
  name: 'IndexPage',
  data(){
    return{
      cards : [
        {id : 1, cardImg : require('../assets/gta6.png'), avatar : "https://cdn.quasar.dev/img/avatar2.jpg", caption : "بررسی دقیق تریلر GTA 6", channelName : "GameStory", viewsAndDate : "93 بازدید 3 روز پیش"},
        {id : 2, cardImg : require('../assets/last2.avif'), avatar : "https://cdn.quasar.dev/img/avatar3.jpg", caption : "لست آف آس | روز بارانی | ساوند ترک", channelName : "Flexin", viewsAndDate : "15K بازدید 3 سال پیش"},
        {id : 3, cardImg : require('../assets/last1.avif'), avatar : "https://cdn.quasar.dev/img/avatar4.jpg", caption : "لست آف آس دو ریمستر شده برای PS5", channelName : "Shirrako", viewsAndDate : "148K بازدید 1 سال پیش"},
        {id : 4, cardImg : require('../assets/atomfall.avif'), avatar : "https://cdn.quasar.dev/img/avatar5.jpg", caption : "اتم فال - قست بقا - بازی اکشن", channelName : "theRadBrad", viewsAndDate : "2.6M بازدید 1 ماه پیش"},
        {id : 5, cardImg : require('../assets/gta6.png'), avatar : "https://cdn.quasar.dev/img/avatar2.jpg", caption : "بررسی دقیق تریلر GTA 6", channelName : "GameStory", viewsAndDate : "93 بازدید 3 روز پیش"},
        {id : 6, cardImg : require('../assets/last2.avif'), avatar : "https://cdn.quasar.dev/img/avatar3.jpg", caption : "لست آف آس | روز بارانی | ساوند ترک", channelName : "Flexin", viewsAndDate : "15K بازدید 3 سال پیش"},
        {id : 7, cardImg : require('../assets/last1.avif'), avatar : "https://cdn.quasar.dev/img/avatar4.jpg", caption : "لست آف آس دو ریمستر شده برای PS5", channelName : "Shirrako", viewsAndDate : "148K بازدید 1 سال پیش"},
        {id : 8, cardImg : require('../assets/atomfall.avif'), avatar : "https://cdn.quasar.dev/img/avatar5.jpg", caption : "اتم فال - قست بقا - بازی اکشن", channelName : "theRadBrad", viewsAndDate : "2.6M بازدید 1 ماه پیش"},
        {id : 9, cardImg : require('../assets/gta6.png'), avatar : "https://cdn.quasar.dev/img/avatar2.jpg", caption : "بررسی دقیق تریلر GTA 6", channelName : "GameStory", viewsAndDate : "93 بازدید 3 روز پیش"},
        {id : 10, cardImg : require('../assets/last2.avif'), avatar : "https://cdn.quasar.dev/img/avatar3.jpg", caption : "لست آف آس | روز بارانی | ساوند ترک", channelName : "Flexin", viewsAndDate : "15K بازدید 3 سال پیش"},
        {id : 11, cardImg : require('../assets/last1.avif'), avatar : "https://cdn.quasar.dev/img/avatar4.jpg", caption : "لست آف آس دو ریمستر شده برای PS5", channelName : "Shirrako", viewsAndDate : "148K بازدید 1 سال پیش"},
        {id : 12, cardImg : require('../assets/atomfall.avif'), avatar : "https://cdn.quasar.dev/img/avatar5.jpg", caption : "اتم فال - قست بقا - بازی اکشن", channelName : "theRadBrad", viewsAndDate : "2.6M بازدید 1 ماه پیش"},
        {id : 13, cardImg : require('../assets/gta6.png'), avatar : "https://cdn.quasar.dev/img/avatar2.jpg", caption : "بررسی دقیق تریلر GTA 6", channelName : "GameStory", viewsAndDate : "93 بازدید 3 روز پیش"},
        {id : 14, cardImg : require('../assets/last2.avif'), avatar : "https://cdn.quasar.dev/img/avatar3.jpg", caption : "لست آف آس | روز بارانی | ساوند ترک", channelName : "Flexin", viewsAndDate : "15K بازدید 3 سال پیش"},
        {id : 15, cardImg : require('../assets/last1.avif'), avatar : "https://cdn.quasar.dev/img/avatar4.jpg", caption : "لست آف آس دو ریمستر شده برای PS5", channelName : "Shirrako", viewsAndDate : "148K بازدید 1 سال پیش"},
        {id : 16, cardImg : require('../assets/atomfall.avif'), avatar : "https://cdn.quasar.dev/img/avatar5.jpg", caption : "اتم فال - قست بقا - بازی اکشن", channelName : "theRadBrad", viewsAndDate : "2.6M بازدید 1 ماه پیش"},
        {id : 17, cardImg : require('../assets/gta6.png'), avatar : "https://cdn.quasar.dev/img/avatar2.jpg", caption : "بررسی دقیق تریلر GTA 6", channelName : "GameStory", viewsAndDate : "93 بازدید 3 روز پیش"},
        {id : 18, cardImg : require('../assets/last2.avif'), avatar : "https://cdn.quasar.dev/img/avatar3.jpg", caption : "لست آف آس | روز بارانی | ساوند ترک", channelName : "Flexin", viewsAndDate : "15K بازدید 3 سال پیش"},
        {id : 19, cardImg : require('../assets/last1.avif'), avatar : "https://cdn.quasar.dev/img/avatar4.jpg", caption : "لست آف آس دو ریمستر شده برای PS5", channelName : "Shirrako", viewsAndDate : "148K بازدید 1 سال پیش"},
        {id : 20, cardImg : require('../assets/atomfall.avif'), avatar : "https://cdn.quasar.dev/img/avatar5.jpg", caption : "اتم فال - قست بقا - بازی اکشن ", channelName : "theRadBrad", viewsAndDate : "2.6M بازدید 1 ماه پیش"},
      ]
    }
  },
  components : {
    MainCard
  }
};
</script>

<style lang="scss" scoped>
  .q-intersection-container{
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 15px;
  }
  @media (max-width:1830px) {
    .q-intersection-container{
      grid-template-columns: repeat(4, 1fr);

    }
  }
  @media (max-width:1530px) {
    .q-intersection-container{
      grid-template-columns: repeat(3, 1fr);

    }
  }
  @media (max-width:1200px) {
    .q-intersection-container{
      grid-template-columns: repeat(2, 1fr);

    }
  }
  @media (max-width:900px) {
    .q-intersection-container{
      grid-template-columns: repeat(1, 1fr);

    }
  }
</style>
