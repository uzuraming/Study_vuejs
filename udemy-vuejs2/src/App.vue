<template>
  <div id="app" class="main">
    <button @click="myAnimation='slide'">slide</button>
    <button @click="myAnimation='fade'">fade</button>
    <p>{{myAnimation}}</p>
    <br>
    <button @click="add">追加</button>
    <ul 
    style="width:200px;
    margin:auto;">
    <transition-group name="fade">
      <li v-for="(number, index) in numbers" :key='number'
      @click="remove(index)">{{ number }}</li>
      </transition-group>
    </ul>
    <button @click="show=!show">切り替え</button>
    <br>
    <transition
      :css="false"
      @before-enter="beforeEnter"
      @enter="enter"

      @leave="leave"

      >
      >
      <div class="circle" v-if="show"></div>
    </transition>

    <button @click="myComponent='ComponentA'">ComponentA</button>
    <button @click="myComponent='ComponentB'">ComponentB</button>    

    <transition name="fade" mode="out-in">
      <component :is="myComponent"></component>
    </transition>


    <transition name="fade" mode="out-in">
      <p v-if="show" key="bye">さよなら</p>
      <p v-if="!show" key="hello">こんにちは</p>
    </transition>
    <transition 
    enter-class=""
    enter-active-class="animate__animated animate__bounce"
    enter-to-class=""
    leave-class=""
    leave-active-class="animate__animated animate__bounce"
    leave-to-class=""
    appear
    >
      <p v-if="show">hello</p>
    </transition>
    
    <transition :name="myAnimation" appear>
      <p v-if = "show">bye</p>
    </transition>
  </div>
</template>

<script>
import  ComponentA  from "./components/ComponentA.vue";
import  ComponentB  from "./components/ComponentB.vue";
export default {
  components:{
    ComponentA,
    ComponentB,
  },
  data(){
    return {
      numbers:[0,1,2],
      nextNumber:3,
      show: true,
      myAnimation:"slide",
      myComponent:"ComponentA",
    }
  },
  methods:{
    randomIndex(){
      return Math.floor(Math.random()*this.numbers.length);
    },
    add(){
      this.numbers.splice(this.randomIndex(),0,this.nextNumber);
      this.nextNumber +=1;
    },
    remove(index){
      this.numbers.splice(index,1)

    },

    beforeEnter(el){
      el.style.transform = 'scale(0)'
    },
    enter(el,done){
      let scale = 0;
      const interval = setInterval(() => {
        el.style.transform = `scale(${scale})`;
        scale+=0.1;
        if (scale>1){
          clearInterval(interval);
          done();
        }
      }, 20);
    },
    // afterEnter(el){},
    // enterCancelled(el){},
    // beforeLeave(el){},
    leave(el,done){
      let scale = 1;
      const interval = setInterval(() => {
        el.style.transform = `scale(${scale})`;
        scale-=0.1;
        if (scale<0){
          clearInterval(interval);
          done();
        }
      }, 20);
    },
    // afterLeave(el){},
    // leaveCancelled(el){},

  },

};

</script>

<style scoped>
.circle{
  width: 200px;
  height: 200px;
  margin: auto;
  border-radius:100px;
  background-color: deeppink;
}

.slide-enter,
.slide-leave-to{
  opacity:0;
}

.slide-enter-active{
  animation:slide-in 0.5s;
  transition: opacity 0.5s;
}
.slide-leave-active{
  animation:slide-in 0.5s reverse;
  transition: opacity 0.5s;
}

@keyframes slide-in{
  from{
    transform: translateX(100px);
  }
  to{
    transform: translateX(0);
  }
}



.fade-move{
  transition: transform 1s;
}
.fade-enter{
  /* 現れる時の最初の状態 */
  opacity:0;
}
.fade-enter-active{
  /* 現れる時のトランジションの状態 */
  transition:opacity 0.5s;
}
.fade-enter-to{
  /* 現れる時の最後の状態 */
  opacity:1
}
.fade-leave{
  /* 消える時の最初の状態 */
  opacity:1
}
.fade-leave-active{
  transition:opacity 0.5s;
  /* 消える時のトランジションの状態 */
}
.fade-leave-to{
  /* 消える時の最後の状態 */
  opacity:0;
}
.main{
  width:70%;
  text-align:center;
  margin:auto;
  padding-top:5rem;
}

</style>
