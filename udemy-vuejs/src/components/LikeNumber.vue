<template>
    <div>  <p>いいね ({{halfnumber}})</p>
  <button @click="increment">+1</button></div>
</template>

<script>
export default{
  props:{
    totalNumber: {
      type: Number,
      required: true,
    }
  },
  computed:{
    halfnumber(){
      return this.totalNumber/2
    }
  },

  methods:{
      increment(){
          this.$emit("my-click",this.totalNumber+1);
      }
  }
}

</script>

<style scoped>

</style>
