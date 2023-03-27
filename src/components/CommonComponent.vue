<template>
  
  	<section :class="{extended:is_extended}">
		<div id="sidebar">
			Side Content
		</div>
		<div id="rightSideWrapper">
			<header> 
				Header 
			</header>
			
			<div class="ContentBox"><!--. poner en minusculas.-->
				<main> 
					Main Content 
				</main>

				<section>
					Section Content
				</section>

				<footer> 
					Footer 
				</footer>

			</div>
			
		</div>
	</section>
</template>

<script>
export default {
name:'SideBar',
props:['navItems'],
data(){
  return{
    // nav_items:[]
    is_extended:true
  }
}

}

</script>

<style lang="scss" scoped>
*{ 
    margin: 0px;
}

#sidebar {
	/*Strictly Necessary */
    width: 100%;
    margin: 0px;
    background: lightblue;
    border-radius: 7px;
}


#rightSideWrapper {
	/*Strictly Necessary */
	width:100%; 
	float: right;

	/*Aesthetics*/
	background: black;	
}

header {
	/*Strictly Necessary */
	height: 100px; /*Adjust the hight to your purposes*/
	
	/*Aesthetics*/
	background: lightSalmon;
	border-radius: 7px;
}

.ContentBox{
	display:flex;
	flex-flow: row wrap;
} 

main, section, footer {
    /*Aesthetics*/
	 background: lightgray; 
	 border-radius: 7px; 
}

main {
  /*Strictly Necessary */
  height: 400px;
  order: 1;
  flex: 0 1 100%; 
	
}

section {
  /*Strictly Necessary */
   order: 2;
   flex: 0 1 100%;
	
}

footer {
  /*Strictly Necessary */
  height: 100px;
  order: 3;
  flex: 0 1 100%;
	
}

.extended{
     display: grid;
    grid-template-columns: 200px auto;  
}

</style>>
