<template>
  <div class="timerList">
    <TimerComponent v-for="{t, index} in timers" :num="t" :key="index" />
    <button class="timerList__add" @click="timers +=1"><AddIcon color="#9E9E9E"></AddIcon></button>
  </div>
</template>

<script>
import TimerComponent from "@/components/TimerComponent";
import AddIcon from "@/components/AddIcon";
export default {
  components:{
    TimerComponent,
    AddIcon
  },
  data(){
    return{
      timers: 5
    }
  }
}
</script>

<style scoped lang="scss">
  .timerList{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 45px 50px;
    width: 780px;
    margin: 0 auto;
    padding:72px 0;
    &__add{
      width: 225px;
      height: 120px;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #696969;
      border: none;
      cursor: pointer;
    }
  }
  @media screen and (max-width: 1023px) {
    .timerList{
      grid-template-columns: 1fr 1fr;
      width: 500px;
    }
  }
  @media screen and (max-width: 767px) {
    .timerList{
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      width: 100%;
    }
  }
</style>