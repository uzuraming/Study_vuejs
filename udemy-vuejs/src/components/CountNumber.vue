<template>
    <div>
        <p v-border:solid.round="{width:'5px',color:'red'}">home</p>>
        <h2>{{title|lowerCase}}</h2>

        
    </div>
    
</template>


<script>
import { tokyoNumber } from "@/tokyoNumber";
export default {
    mixins:[tokyoNumber],
   

}
    

</script>