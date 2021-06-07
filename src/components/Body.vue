<template >

  <div id="container">
    <div class="squares">
      <Square :color="colors[0]" />
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
    props: ['isHard'],
    beforeMount(){
      this.$parent.$on('resetear',this.changeData)
    },
    mounted () {
      this.init()
    },
    components:{
      Square
    },
    data () {
      return {
        colors:[],
        pickedColor:"",
        esDificil:true,
      }
    },
    methods: {
      init(){
        this.colors = this.createNewColors(this.esDificil)
        this.pickedColor = this.colors[this.pickColor()]
        this.$emit('colorElegido',this.pickedColor)
        console.log(this.pickedColor);
      },
      createNewColors(bool){
        let numbers= bool ? 6 : 3
        console.log(numbers);
        var arr = [];
        for (var i = 0; i < numbers; i++) {
          arr.push(this.createRandomStringColor());
        }
          return arr;
      },
      createRandomStringColor(){
        var newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
        return newColor;
      },
      randomInt(){
        return Math.floor(Math.random() * 256);
      },
      pickColor(){
        let cantidad= this.esDificil? 6 : 3 
        let number= Math.floor(Math.random() * cantidad);
        console.log('NUMERO COLOR',number);
        return number
      },
      changeData(estado){
        this.esDificil=estado
        this.init()
      },
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
