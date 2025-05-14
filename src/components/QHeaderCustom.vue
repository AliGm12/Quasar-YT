<template>
  <q-btn
    flat
    dense
    round
    icon="menu"
    aria-label="Menu"
      @click="$emit('hideSidebar')"
  />
</template>

<script>
export default {
name : 'QHeaderCustom'
}
</script>

<style lang="scss" scoped>

</style>
