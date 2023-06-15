<template>
<footer>
    <p class="texte_droit">
        <h2>Tous les drois  sont resverd </h2>
    </p>
    <ul class="ul_footer">
        <li><a href="#">Termes et Conditions</a></li>
        <li><a href="#">Politique de confidentialité</a></li>
        <li><a href="#">Gérer les cookies</a></li>
        <li> <a href="#">Risques</a></li>
    </ul>
</footer>
</template>
<script>

</script>
<style scoped>
footer{
    color: white;
   background-color: #1EA896; 
   height:13vh;
   display: flex;
   align-items: center;
   width:100%;
}
.ul_footer{
    height:13vh;
    /* background-color: aqua; */
   display: flex;
   width: 80%;
   justify-content: space-around;
   align-items: center;
   margin-left: 2em;
}
.ul_footer a {
    font-size:1.4em;
    color: white;
}

.texte_droit{
    margin-left: 2em;

}
@media only screen and (max-width: 640px){
    footer{
        background-color: black;
        width:100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
   .ul_footer{
    display: none;
   }  


  
}
</style>