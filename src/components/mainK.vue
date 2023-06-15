<template>
 <main>
    
    <div id="contenu_article" >
        <div class="boucle_for" v-for="tous_les_article in tous_les_article" >

       
        <RouterLink :to="'/Article/' + tous_les_article.id">
    <div class="divison_2"  >
      <p>
        <img :src="tous_les_article.image" alt="" height="400" width="600">
      </p>    
       <h1 class="color_white" id="H1premier">{{ tous_les_article.sous_titre}}</h1>
      
      </div>
      <br>
      <h2 class="titre">{{ tous_les_article.titre }}</h2>
    </RouterLink>
    </div>

      <div class="bar_horizontal">
       <button class="droite"><img src="../components/icons/Polygon1.png" alt=""></button>
       <div class="contenu">
        
       <div class="article_barre_horizental" v-for="micro_article in micro_article">
        <RouterLink :to="'/Article/' + micro_article.id">
      <p><img :src="micro_article.image" alt="" height="150" width="150"></p>
      <br>
      <p class="H1_text_center"><h1 class="color_white">{{ micro_article.sous_titre }}</h1></p>
    </RouterLink>
       </div>
    </div>
       <button class="gauche"><img src="../components/icons/Polygon2.png" alt=""></button>

      </div>
       
        
    </div>
    <div id="bar_verticale">
        <div class="tex_center">
        <h1 >Liste des cryto  selon  parts </h1>
        </div>
        <div class="goblal">
    <div class="graphique">
        <canvas id="myChart"></canvas>
    </div>
</div>
    <div class="formations">
        <p>
            <h1>FORMATIONS TRADING</h1>
        </p>
        <p class="image_formation">
            <img src="../assets/pexels-rdne-stock-project-6517084.jpg" alt="">
        </p>
    </div>
  
</div>


   
 </main>
</template>
<script>
import axios from 'axios';
import { RouterLink } from 'vue-router'
export default{
   
    data(){
        return{
            tous_les_article: [],
            micro_article:[]

        }
    },mounted(){
        const ctx = document.getElementById('myChart');
        new Chart(ctx, {
  type: 'pie',
  data: {
    labels: ['bitcoin', 'Ethereum', 'ada','Tether','Litecoin','USD Coin'],
    datasets: [{
      data: [200, 150, 80,50,130,146],
      backgroundColor: ['#61A0AF', '#F06C9B', '#96C9DC','#003049','#2a9d8f','#c1121f']
    }]
  },
  options: {
    responsive: true,
    plugins: {
      tooltip: {
        enabled: true,
        caretPadding: 4
      }
    }
  }
});

axios.get('/article1.json')
  .then((response) => {
    this.tous_les_article = response.data.Article;
  })
  .catch((error) => {
    console.error(error);
  });

  axios.get('/article_image.json')
  .then((response) => {
    this.micro_article = response.data.Article;
  })
  .catch((error) => {
    console.error(error);
  });

const contenu = document.querySelector('.contenu');
const droite = document.querySelector('.droite');
const gauche = document.querySelector('.gauche');

  function namek() {
    contenu.addEventListener('wheel',(evt)=>{
        evt.preventDefault();
        contenu.scrollLeft += evt.deltaY;
    })
  };


  function clik_droite(){
    droite.onclick = () => {
        contenu.scrollLeft -= 920;
      };
  };
  function click_gauche(){
       gauche.onclick = () => {
        contenu.scrollLeft += 920;
      };
  };
  click_gauche()
  clik_droite()
  namek()
//         evt.preventDefault();
//         container.scrollLeft += evt.deltaY;
// });


}
,methods:{



    }

}
  
</script>
<style>
main{
    height:auto;
    display: flex;
    background-color: red;
    width: 100%;
}
#contenu_article{
    background-color:white;
    width:70%;
}
.divison_2{
    padding-top:2%;
background-color:white;
display:flex;
justify-content: space-around;
align-items: center;
}

.color_white{
    color:#9F6BA0;
    /* background-color: red; */
    overflow: hidden;
    white-space: nowrap;
    font-size: 1.7em;
    font-weight: bold;
    text-decoration: underline;
}
.titre{
    color: black;
}
#bar_verticale{
    background-color:white;
    width: 30%;
    border-left: 2px solid black ;
}
.goblal{
    /* background-color: azure; */
    display: flex;
    justify-content: center;
    align-items: center;
}
.graphique{
    width:30em;
    height:30em;
    /* background-color: aqua; */
    
}

.tex_center{
height:7vh;
display: flex;
justify-content: center;
align-items: center;
/* background-color: red; */
}
.formations{
    /* background-color: blue; */
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top:2em;
    margin-bottom:2em;
}
.image_formation img{
    width:250px;
    height:130px;
}
.bar_horizontal{
    /* background-color: red; */
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin-top: 6%;
}
.article_barre_horizental{
     /* display: flex; */
    /* background-color: aqua; */
    /* justify-content: center;
    align-items: center; */
     padding: 14px;
}
.contenu{
    display: flex;
    width: 695px;
    /* background-color: blue; */
    overflow: hidden;
}
.H1_text_center{
    /* background-color:red; */
    text-align: center;
}
.color_white{
    color:black;
}
.droite,.gauche{
    background-color:transparent;
    border: none;

}
#H1premier{
    color: #9F6BA0;
}
</style>