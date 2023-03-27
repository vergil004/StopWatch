<template>
  <div class="watch" :class="{'watch--active': isActive}">
    <div class="watch__time">
      <div v-if="hours">{{hours}}:</div>
      <div v-if="minutes"><span v-if="minutes < 10">0</span>{{minutes}}:</div>
      <div><span v-if="seconds < 10">0</span>{{seconds}}</div>
    </div>
    <div class="watch__bottom">
      <button @click="start" class="watch__btn" :disabled="isClicked">
        <StartIcon v-if="!isActive" :color="iconColor"/>
        <PauseIcon v-else :color="iconColor"/>
      </button>
      <button class="watch__btn" @click="stop">
        <StopIcon :color="iconColor"/>
      </button>
    </div>
  </div>
</template>

<script>
import StartIcon from '@/components/StartIcon';
import PauseIcon from "@/components/PauseIcon";
import StopIcon from "@/components/StopIcon";

export default {
  props:{
    num:Number
  },
  components:{
    StartIcon,
    PauseIcon,
    StopIcon
  },
  computed:{
    iconColor(){
      return this.isActive ? '#ffffff' : '#9E9E9E'
    }
  },
  data(){
    return{
      hours: 0,
      minutes: 0,
      seconds: 0,
      isActive: false,
      isClicked: false
    }
  },
  methods:{
    start(){
      this.isActive = !this.isActive;
      this.isClicked = true;
      const interval = setInterval(() => {
        if(!this.isActive){
          clearInterval(interval)
        }else{
          if(this.seconds === 59){
          this.seconds = 0
          this.minutes += 1;
        }
        if(this.minutes === 59){
          this.hours += 1;
        }
        this.seconds +=1;
        }
      }, 1000)
      setTimeout(() =>{
        this.isClicked = false
      },1000)
    },
    stop(){
      this.isActive = false;
      this.hours = 0;
      this.minutes = 0;
      this.seconds = 0;
    }
  }
}
</script>

<style scoped lang="scss">
.watch{
  width: 225px;
  height: 120px;
  background-color: #696969;
  &__time{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 60px;
    border-bottom: 1px solid #9E9E9E;
    font-family: "Gotham Pro";
    font-weight: 400;
    font-size: 22px;
    color: #9E9E9E;
  }
  &__btn{
    background: none;
    border: none;
    color: #9E9E9E;
    width: 20px;
    height: 20px;
    cursor: pointer;
    display: flex;
    justify-content: center;
    padding: 0;
  }
  &__bottom{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 60px;
    gap: 0 48px;
  }
  &--active{
    .watch__time{
      border-color:#fff;
      color: #ffffff;
    }
  }
}
</style>