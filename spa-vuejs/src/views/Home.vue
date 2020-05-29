<template>
    <div>
        <h1>Home</h1>
        <button @click="toUsers">Usersページに行く</button>
    </div>
</template>

<script>
export default{
    methods:{
        toUsers(){
            this.$router.push('users')
        }

    }
}

</script>