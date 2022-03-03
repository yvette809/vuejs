<template>
<p>Reaction time -{{score}} ms</p>
    
</template>


<script>
export default {
    props:['score'],
    data(){
        return{
            rank:null
        }

    },
    mounted(){
        if(this.score<250){
            this.rank= 'Ninja fingers'
        }else if(this.score<400){
            this.rank ='rapi felexes'
        }else{
            this.rank = 'snail pace...'
        }
    }
}
</script>


<style scoped>

</style>