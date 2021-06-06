<template >

  <div id="container">
    <div class="squares">
      <Square/>
      <Square/>
      <Square/>
    </div>   
    <div v-show="son6" class="squares">
      <Square/>
      <Square/>
      <Square/>
    </div>   
  </div>

</template>

<script>

  import Square from "./Square.vue";

  export default  {
    name: 'body',
    props: ['isHard'],
    mounted () {

    },
    components:{
      Square
    },
    data () {
      return {
        son6:this.isHard,
        // colorElegido:this.pickColor(),
      }
    },
    methods: {
      // pickColor(){
        
      // }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
#container {
	margin: 20px auto;
	max-width: 600px;
} 
</style>
