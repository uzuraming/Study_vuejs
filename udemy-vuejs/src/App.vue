<template>
  <div>
    <LikeHeader>
      <h3>はじめまして</h3>
    </LikeHeader>
    
        <LikeNumber :total-number="number" @my-click="number=$event"></LikeNumber>
        <LikeNumber :total-number="number"></LikeNumber>
        <button @click="currentComponent='Home'">Home</button>
        <button @click="currentComponent='About'">About</button>
        <keep-alive>
          <component :is="currentComponent"></component>
        </keep-alive>

        <div>
          <h2>イベントのフォーム</h2>
          <label for="title">タイトル</label>
          <input
            id="title"
            type="text"
            v-model.lazy="eventData.title"
            >
          <p>{{eventData.title}}</p>

          <h2>イベントのフォーム</h2>
            <label for="title">タイトル</label>
            <input
              id="maxNumber"
              type="number"
              v-model.number="eventData.maxNumber"
              >
          <p>{{eventData.maxNumber}}</p>

          <label for="title">主催者</label>
            <input
              id="host"
              type="text"
              v-model.trim="eventData.host"
              >
          <p>{{eventData.host}}</p>

          <label for="detail">イベントの内容</label>
          <textarea id="detail" cols="30" rows="10" v-model="eventData.detail"></textarea>
          <pre>{{eventData.detail}}</pre>
          <input type="checkbox" id="isPrivate" v-model="eventData.isPrivate">
          <label for="isPrivate">非公開</label>
          <p>{{eventData.isPrivate}}</p>
          <p>参加条件</p>
          <input type="checkbox" id="10" value="10代" v-model="eventData.target">
          <label for="isPrivate">10代</label>
          <input type="checkbox" id="20" value="20代" v-model="eventData.target">
          <label for="isPrivate">20代</label>
          <input type="checkbox" id="30" value="30代" v-model="eventData.target">
          <label for="isPrivate">30代</label>
          <p>{{eventData.target}}</p>

          <p>参加費</p>
          <input type="radio" id="free" value="無料" v-model="eventData.price">
          <label for="free">無料</label>
          <input type="radio" id="paid" value="有料" v-model="eventData.price">
          <label for="paid">有料</label>
          <p>{{eventData.price}}</p>


          <select v-model="eventData.location">
            <option
              v-for="location in locations"
            :key="location">{{location}}</option>
          </select>
          <p>{{eventData.location}}</p>

        </div>


  </div>
</template>

<script>
import LikeHeader from "./components/LikeHeader.vue";
import About from "./components/About.vue";
import Home from "./components/Home.vue";
export default{
  data(){
    return{
      number:10,
      currentComponent:"Home",
      locations:["東京","大阪"],
      eventData:{
        title:"タイトル",
        maxNumber:0,
        host:"",
        detail:"",
        isPrivate:false,
        target:[],
        price:"無料",
        location:"東京"
      }

    }
  },
  components:{
   LikeHeader:LikeHeader,
   About:About,
   Home:Home
 }

}

</script>

<style scoped>


</style>

