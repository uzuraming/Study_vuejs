<template>
    <div>
        <h1>Users</h1>
        <router-link to="/users/1">ユーザー１</router-link>
        <router-link to="/users/2">ユーザー２</router-link>
        <hr>
        <h1>User no.{{id}}</h1>
    </div>
</template>

<script>
export default{
    props:["id"],
}

</script>
