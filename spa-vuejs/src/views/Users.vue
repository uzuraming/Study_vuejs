<template>
    <div>
        <h1>Users</h1>
        <router-link to="/users/1">ユーザー１</router-link>
        <router-link to="/users/2">ユーザー２</router-link>
        <hr>
        <h1>User no.{{id}}</h1>
        <router-link :to="'/users/' + (Number(id) + 1) +'/profile'">次のユーザー</router-link>
        <router-link :to="{ name: 'users-id-profile', params: { id: Number(id) + 1}}">次のユーザー</router-link>
        <router-view></router-view>
    </div>
</template>

<script>
export default{
    props:["id"],
    beforeRouteEnter(to,from,next){
        next(vm => {
            console.log(vm.id)
        });
    },
    beforeRouteUpdate(to,from,next){
        console.log('beforeRouteUpdate');
        next();
    },
    beforeRouteLeave(to,from,next){
        console.log('beforeRouteLeave');
        const isLeave = window.confirm('このページを離れますか？');
        if(isLeave){
            next()
        }else{
            next(false)
        }
    }
}

</script>
