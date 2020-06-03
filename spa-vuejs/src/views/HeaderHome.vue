<template>
    <nav >
        <h2>Users</h2>
      <router-link to="/"
      class="link"
      active-class="link--active"
      exact>Home</router-link>
      <router-link to="/users"
      class="link"
      active-class="link--active"
      >Users</router-link>
      <button @click="increment">+1</button>
      <button @click="decrement">-1</button>

    </nav>
</template>

<script>
export default{
  methods:{
    increment(){
      this.$store.state.count++
    },
    decrement(){
      this.$store.state.count--
    }
  },
}
</script>