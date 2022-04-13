<template>
    <header>
      <h1 id="header1">Coding Trello</h1>
      <button id="button1" @click="addCategorie">Ajouter Categorie</button>
    </header>
    <div id="listCat">
      <categorie-comp v-bind:categorie="categorie" v-for="(categorie,index) in categories" :key="categorie.id" @remove="removeCat(index)"/>
    </div>
</template>


<script>

import CategorieComp from '../components/NewCategorie.vue'

export default {
  name: 'HomeView',
  components: { 
    CategorieComp,
  },
  data() {
    return{
      categories :[],
      counter:1,
    }
  },
  
  methods: {
      addCategorie(){
        this.categories.push({title:'', body:'', id: this.counter++});
      },

    removeCat(index){
            console.log(index)
            this.categories.splice(index,1)
        }
    }
}

</script>


<style>
body{
  margin: 0; 
  padding:0; 
  width: 100%; 
  height: 100vh; 
  overflow: hidden;
  background-color: grey;
  }

#app {
  margin-top: 0;
  margin-left: 0;
  width: 100%;
  height: 100vh;
   background-image: 
    linear-gradient(62deg,rgba(7,86,160,0.973) 13%, rgba(255,122,151,0.5) 4%),
    linear-gradient(44deg, rgba(0,43,99,0.079) 13%, rgba(242,140,143,0.5) 18%),
    linear-gradient(118deg, rgba(84,202,242,0.031) 40%, rgba(247,155,187,0.5) 54%),
    linear-gradient(58deg,rgba(90,90,237,0.161) 83%, rgba(249, 156, 142, 0.5) 24%);
    background-blend-mode: normal,lighten,multiply,hard-light;
  position: sticky;
  padding:0;
}

#header1{
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color:black;
}

header{
  
  top: -2.2%;
  left: 0;
  margin:0;
  padding: 0;
  height: 10%;
  position:sticky;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  flex-direction: row;
  gap: 38%;

}
#button1{
  margin-right: 4%;
}

#listCat{
  
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  margin: 1%;
  width: 95%;
  padding-left: 3%;
  border-radius:10px;
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  position: sticky;
  overflow: hidden;
}
button{
  background-color: rgba(255,255,255,0.3);
  border: 0.5px solid black;
  color: black;
  font-weight:500;
  border-radius: 20px;
  cursor: pointer;
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
::placeholder{
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
@media (max-width: 640px){
  #listCat{
    display: flex;
    flex-direction: column;
    
  }
  #app{
    position:fixed;
    overflow: scroll;
  }
  #listCat{
    width: 350%;
  }
  #creator{
    width: 100%;
  }
  #titlePost{
    width: 70%;
  }
}


</style>
