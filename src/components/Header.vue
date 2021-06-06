<template>

<section class="header">
  <div id="header">
		<h1>The Great <br>
			<span id="colorDisplay">RGB</span>
			<br>
			Guessing Game</h1>
	</div>
  <Navbar/>
</section>

</template>

<script>

  import Navbar from "./Navbar.vue";

  export default  {
    name: 'header',
    props: [],
    mounted () {
      
    },
    components:{
      Navbar
    },
    data () {
      return {
          
      }
    },
    methods: {
      
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
#header {
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
