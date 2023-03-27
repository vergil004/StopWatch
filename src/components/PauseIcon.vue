<template>
  <svg width="10" height="20" viewBox="0 0 10 20" :fill="color" xmlns="http://www.w3.org/2000/svg">
    <rect x="7" width="3" height="20" :fill="color"/>
    <rect width="3" height="20" :fill="color"/>
  </svg>
</template>

<script>
export default {
  props:{
    color: String
  }
}
</script>

<style scoped>

</style>