<template>
    <RouterView/> 
<nav>
    <button class="clik" type="button"><a href="#nav"><img src="..\assets\icons8-menu-50.png" alt=""></a></button>
    <ul class="menu">
       
        <li> <RouterLink to="/">Accueil </RouterLink></li>
        <li><RouterLink to="/blog">Blog</RouterLink></li>
        <li><RouterLink to="/contacte">Contacte</RouterLink></li>
        <button class="x" id="efface"><a href="#"> <img src="..\assets\icons8-x-50.png" alt=""></a>   </button>
    </ul>
</nav>
</template>
<script>
  import {RouterLink} from 'vue-router';
export default{
    data(){
  return{

  }
    },
    mounted(){

        const clik = document.querySelector('.clik')
        const menu = document.querySelector('.menu')
        const x = document.querySelector('.x')

        const screenk = screen.width  >=  600

        clik.addEventListener('click',myfunction)
      function myfunction(){
      
        menu.style.display ='flex'
        clik.style.display ='none'
        x.style.display ='flex'
        
      };
      x.addEventListener('click',myfunction2 )
      function myfunction2(){
    
        menu.style.display ='none'
        clik.style.display ='block'
      }

      function checkWindowSize() {
  if (window.innerWidth < 640) {
    // La taille de la fenêtre est inférieure à 650 pixels
    shouldReload = true;
  } else if (shouldReload) {
    // La taille de la fenêtre est supérieure à 650 pixels et devrait être rechargée
    location.reload();
  }
}

var shouldReload = false;
window.addEventListener("resize", checkWindowSize);






    //  s myfunction()
    //   myfunction2()var element = document.getElementById("votreElement"); // Remplacez "votreElement" par l'ID de votre élément



    },
    methods:{

    }
}
</script>
<style scoped>
nav{
    height:13vh;
     background-color:#2C191A;
    width:100%; 
}
ul{
    height:13vh;
    width:100%; 
    display: flex;
    justify-content: space-around;
    align-items: center;
}
a {
font-size: 2em;
color: white;

}
.clik{
    display: none;
}
.x{
    display: none;
}


@media only screen and (max-width: 640px) {

    nav{
        height:auto;
        background-color: #1EA896;
    }
  ul{
    height: 30vh;
     justify-content: space-around;
    display: flex;
    flex-direction: column;
   
   background-color:#1EA896;
  }
  li{
    /* padding-top:4em;
    padding:1em; */
    font-size: 1.2em;
  }

  .clik{
    display:block;
    height: 5em;
    padding:5px;
    color: white;
    background-color:#1EA896;
    border: none;
    cursor: pointer;
}
.clik img{
  height: 45px;
  width:45px;
}
ul{
    display: none;
}
.x img{
    height: 20px;

}
.x{
    border: none;
    cursor: pointer;
    background-color: transparent;
}
}

</style>