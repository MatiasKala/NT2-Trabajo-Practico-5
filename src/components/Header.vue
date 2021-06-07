<template>

<section class="headerStyle">
  <div id="headerStyle">
		<h1>The Great <br>
			<span id="colorDisplay">RGB {{colorElegido}}</span>
			<br>
			Guessing Game</h1>
	</div>
  <Navbar @colorElegidoHeader="setColorElegido($event)" />
</section>

</template>

<script>

  import Navbar from "./Navbar.vue";

  export default  {
    name: 'header-component',
    props: [],
    mounted () {
      
    },
    components:{
      Navbar
    },
    data () {
      return {
        colorElegido:""
      }
    },
    methods: {
      setColorElegido(color){
        this.colorElegido = color.slice(3)
      },
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
#headerStyle {
	transition: all 0.3s;
	background: steelblue;
	text-transform: uppercase;
	text-align: center;
	margin: 0;
	color: white;
	
}
#colorDisplay {
	font-size: 200%;
}
</style>
