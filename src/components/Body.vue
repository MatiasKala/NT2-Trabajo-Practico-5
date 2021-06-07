<template >

  <div id="container">
    <div class="squares">
      <Square :color="colors[0]"/>
      <Square :color="colors[1]"/>
      <Square :color="colors[2]"/>
    </div>   
    <div v-show="isHard" class="squares">
      <Square :color="colors[3]"/>
      <Square :color="colors[4]"/>
      <Square :color="colors[5]"/>
    </div>   
  </div>

</template>

<script>

  import Square from "./Square.vue";

  export default  {
    name: 'body-component',
    props: ['isHard','cantidadCuadrados'],
    mounted () {
      
    },
    components:{
      Square
    },
    data () {
      return {
        colors: this.createNewColors(this.cantidadCuadrados),
      }
    },
    methods: {
      createNewColors(numbers){
        var arr = [];
        for (var i = 0; i < numbers; i++) {
          arr.push(this.createRandomStringColor());
        }
          return arr;
      },
      createRandomStringColor(){
        var newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
        console.log(newColor);
        return newColor;
      },
      randomInt(){
        return Math.floor(Math.random() * 256);
      },
      pickColor(){
        return Math.floor(Math.random() * this.cantidadCuadrados );
      }
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
