<template>
    <div  class="second-part row justify-between">
      <div class="q-gutter-none">
        <p :class="['q-my-none', index == 0 ? 'text-bold text-subtitle1' : 'text-normal']"
         v-for="(item, index) in captions" :key="index">
            {{ item }}
        </p>
      </div>
      <q-icon size="16px" name="fa-solid fa-ellipsis-vertical"></q-icon>
    </div>
</template>

<script>
  export default{
    name : 'CardCaption',
    props : {
      captions : Array
        }
  }
</script>

<style lang="scss" scoped>
  .second-part{
    width: 100%;
    flex-wrap: nowrap;
  }
</style>
