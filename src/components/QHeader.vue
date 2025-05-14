<template>
      <q-btn
        flat
        dense
        round
        icon="menu"
        aria-label="Menu"
          @click="miniState = true;showBtnFunc()"
      />
</template>

<script>
  export default {
    name : 'QHeader'
  }
</script>

<style lang="scss" scoped>

</style>
