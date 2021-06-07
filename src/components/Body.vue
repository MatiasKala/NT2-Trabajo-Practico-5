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
    updated(){
      // console.log('Es dificil Updated ',this.esDificil);
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
      },
      createNewColors(bool){
        console.log('CREATE NEW', bool);
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
        return Math.floor(Math.random() * this.isHard? 6 : 3 );
      },
      reset(){
        this.colors = this.createNewColors(this.esDificil)
        this.pickedColor = this.colors[this.pickColor()]
      },
      changeData(estado){
        this.esDificil=estado
        console.log('ES DIFICIL ',estado);
        this.reset()
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
