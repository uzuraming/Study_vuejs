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
      <button @click="increment(2)">+1</button>
      <button @click="decrement(2)">-1</button>

    </nav>
</template>

<script>
import { mapActions } from "vuex";
export default{
  methods:{
    ...mapActions(["increment","decrement"]),

    
  },
}
</script>