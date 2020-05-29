<template>
    <div>
        <p v-border:solid.round="{width:'5px',color:'red'}">home</p>>
        <h2>{{title|lowerCase}}</h2>
        <CountNumber></CountNumber>

        
    </div>
    
</template>


<script>
import CountNumber from "./CountNumber.vue";
import { tokyoNumber } from "@/tokyoNumber";
export default {
    components:{
        CountNumber
    },
    mixins:[tokyoNumber],
    data(){
        return{
         
        }
    },
    directives:{
        border(el,binding){
              el.style.border="solid black 2px";
                el.style.borderWidth=binding.value.width
                el.style.borderColor=binding.value.color;
                el.style.borderStyle=binding.arg;
                if(binding.modifiers.round){
    el.style.borderRadius = "0.5rem"
        }     
        },
    },
    

}
    

</script>