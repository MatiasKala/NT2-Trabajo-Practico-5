<template>

  <div id="navigator">
		<button id="reset"> New colors</button>
		<span id="message"> </span>

		<button id="easy">easy</button>
		<button id="hard" class="selected">hard</button>
    <Body :isHard="isHard"/>
	</div>

</template>

<script>

  import Body from "./Body.vue";

  export default  {
    name: 'navbar',
    props: [],
    mounted () {

    },
    components:{
      Body
    },
    data () {
      return {
        isHard:true
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
#navigator {

	background: #ffffff;
	height: 30px;
	text-align: center;
	margin: 0;
	margin-top: -30px;

}
#message {
	color: #ffffff;
	display: inline-block;
	width: 20%;
}
button {
	border: none;
	background-color: white;
	font-family: "Montserrat", "Avenir";
	text-transform: uppercase;
	height: 100%;
	font-weight: 700;
	letter-spacing: 1px;
	color: steelblue;
	transition: all 0.3s;
	outline: none;
}
button:hover {
	color: white;
	background-color: steelblue;
}
.selected {
	background-color: steelblue;
	color: white;
}
</style>
