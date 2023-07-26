
<template>
    <div id="container">
      <div id='firstline'> 
          <div class="menu">
              
              <ul id='intranet_menu'>
                  <li> <NuxtLink to="/intranet/">  Intranet</NuxtLink>  </li>
                  <li> <NuxtLink to="/people/">  People</NuxtLink> </li>
                  <li> <NuxtLink :to="`/contact/`"> Contact </NuxtLink></li>
                  <li> FR </li>
              </ul>
          </div>
          <div id='search_container'>
              <div id="second_container">
                  <font-awesome-icon class="icon" icon="fas fa-search" />
                  <input id="search_input" type="text" name="search">
              </div>
          </div>
  
      </div>
      <div id='secondline'> 	
          <div id="logo_container">
              <NuxtLink to="/"> <img src="/icr.png"></NuxtLink> 
          </div>
          
  
          <div class="menu" id ='menu_container'>
              
                  <ul id='main_menu'>
  
                      <li> Institute <font-awesome-icon class="icon" icon="fas fa-caret-down" />
                          <ul>
                              <li><NuxtLink :to="`/people/`"> Directory</NuxtLink></li>
                              <li><NuxtLink :to="`/contact/`"> Contact </NuxtLink></li>
                          </ul>
                      </li>
                      <li><NuxtLink to="/teams/">  Teams  </NuxtLink><font-awesome-icon class="icon" icon="fas fa-caret-down" />
                              <ul>
                                  <li v-for="post in teams" :key="post.id" :post="post" class="menu__group"> 
                                      <NuxtLink :to="`/teams/${post.slug}`"> {{post.acf.team_name}}</NuxtLink>
                                  </li>
                              </ul>
                      </li>
                      <li> <NuxtLink to="/publication/">  Publications</NuxtLink></li>
                      <li> <NuxtLink :to="`/news/`"> News </NuxtLink> </li>
                      <li> <NuxtLink :to="`/event/`"> Event </NuxtLink> </li>
                      <li> Platform<font-awesome-icon class="icon" icon="fas fa-caret-down" />
                          <ul>
                              <li><NuxtLink :to="`/platform/RPE`"> RPE Common services </NuxtLink></li>
                              <li><NuxtLink :to="`/platform/Polymer`"> Polymer Analysis </NuxtLink></li>
                          </ul>
  
                      </li>
                      <li><NuxtLink :to="`/job/`"> Job </NuxtLink> </li>
                  </ul>
          </div>	
      </div>
  </div>
  </template>

 <script setup>
import axios from "axios";

const teams = ref();

axios.get("https://icr.rubidiumweb.eu/wp-json/wp/v2/team").then((response) => {
	teams.value = response.data})
console.log(teams)
console.log("sdfsf")
</script>







<style  lang="scss"  scoped>

#container{

	border-bottom: 1px solid #d48536;
	width: 100%;
	position:sticky;
	top:0px;
	background-color: white;
	z-index:1000;

}
#firstline{
	display: flex;
	justify-content:space-between;
	height:100px;
	padding: 10px;

}

#secondline{
	display: flex;
	justify-content:space-between;
	height:100px;
	
}


#intranet_menu{
	display: flex;
	
}

#intranet_menu li{
	padding: 10px;
	font-family: "Lato", Sans-serif;
	font-size: 15px;
	font-weight: 400;
	
}
#intranet_menu li:hover{
	color:#d48536;

}

#main_menu{
	display: flex;
	flex-wrap: wrap;
	font-family: "Lato", Sans-serif;
	font-weight: 500;
	
}

.menu a{
	color:black;
 	 border-width:10px;
 	 text-decoration: none;
	 
	
}



#main_menu li{
	padding: 20px;
	// border-bottom: 3px solid white;
	display: flex;
	position:relative;
	text-transform: uppercase;
}

#main_menu>li:hover{
	color:#d48536;
	border-bottom: 3px solid #d48536; 
}




#main_menu li ul {
	
	position:absolute;/*position it absolutely..*/
	left:0px;/*...align the left edge with the left edge of the parent li...*/
	top:61px;/*...and 32px down from the top - 30px height + 2px for the border */
	// display:none; 

	visibility: hidden;
  	opacity: 0;
  	transition: visibility 0s, opacity 0.1s linear;
}

#main_menu li:hover ul{
	display: table;
    border-collapse: collapse;
	box-shadow: -10px 10px 20px rgba(128, 128, 128, 0.386), 10px 10px 20px rgba(128, 128, 128, 0.386);
	visibility: visible;
  	opacity: 1;
}

#main_menu li ul li {
	transition-delay: 250ms;
	background-color:white;
	padding:15px 10px 15px 10px;
	border-bottom: 1px solid rgba(0, 0, 0, 0.325);
    overflow: hidden;
    white-space: nowrap;
	text-transform: capitalize;
}

#main_menu li ul li div{
height: 32px;
}




a:hover{
	color:#d48536;
}



ul,li{
	list-style-type: none;
	
	
}



#search_container{
	margin-right:10% ;
	margin-top: 10px;
}

#menu_container{
  height: 100px;
  position: relative;
}

.icon{
	margin-left: 10px;
}

</style>
