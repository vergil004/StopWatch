<template>
  <svg width="20" height="20" viewBox="0 0 20 20" :fill="color" xmlns="http://www.w3.org/2000/svg">
    <rect x="8.5" width="3" height="20" :fill="color"/>
    <rect y="11.5" width="3" height="20" transform="rotate(-90 0 11.5)" :fill="color"/>
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