<template>
<div>
        <div id="back">
            <div class="post">

                <!-- Boutton -->
                <span><button id="btn" class="btn btn-danger" @click="closePost(post)">❌</button>
                <button id="btn" @click="openEdit(pos)" class="btn btn-secondary"><span v-if="showedit">Close Update</span>
                <span v-else>Update</span></button></span>
                <div>
                <br>

                <!-- Elements à afficher -->
                
                <p contenteditable="">{{post}}</p>
                <br>    
                <textarea contenteditable="">Votre description</textarea>
                </div>
                
                <!-- Appel Edit -->
                <EditPost v-if="showedit" :idedit='idedit'/>
                
                <div id="com-space"></div>
                <p>Commentaires :</p>
            
            <ul>
                <li v-for="com in coms" :key="com.id" contenteditable="">{{com.commentaire}}</li>
            </ul>
            
                <div>

                    <input id="titleComm" v-model="formccontent" placeholder="Entrer un nouveau Commentaire">
                    <button id="bt1" @click="addComm">Ajouter une Commentaire</button>
        
                <!--<span><input type="text" v-model="formc.content"/> <button @click="addComm()" class="btn btn-light">Comment</button></span>
                    <span v-if="showeditC"><input type="text" v-model="formedit.content" /><button @click="submiteditC(idc)" class="btn btn-light">Edit</button></span>
                    <div id="com" v-for="com in coms" v-bind:key="com.id">
                        <a @click="deleteCo(com.id)">Delete your com</a> | <a @click="editC(com.id)">Edit your com</a>
                        <p>From : {{com.author_name}}</p>

                        V-html pour enlever les balises <p> sur le display
                        <p v-html="com.content.rendered"></p>
                    </div>-->
                </div>
            </div>
        </div>
    </div>
</template>


<script>


export default {
    name : 'EditPost',
    props : [
      'post',
    ],
    data() {
      return {
        titlep:'',
        description: "Test",
        idedit: '',
        showedit: false,
        showeditC: false,
        idc: '',
        coms: [],
        formedit: {
            content: '',
        },
        counter:1,
      }
    },
    //UTILISATION DE L'API

    /*mounted() {
      WPapi.getpost(this.pos)
      .then(response => {
        this.description = response.data.content.rendered;
        this.title = response.data.title.rendered;
      })
      .catch(error => {
      console.log('Error :', error.response)
      }),
      WPapi.getcoms(this.pos)
      .then(response => {
        this.coms = response.data
      })
      .catch(error => {
      console.log('Error :', error.response)
      })

    },*/
    methods: {
    closePost() {
        this.$emit('closePost');
    },
    addComm(){
            this.coms.push({commentaire:this.formccontent,id:this.counter++})    
        },
    }
    /*
    openEdit(id) {
      if (this.showedit === true) {
      this.showedit = false;
      }
      else {
      this.showedit = true;
      this.idedit = id
      }
    },
    
    deletePo(id) {
        WPapi.deletePo(id)
        .then(function( response ){
            console.log(response)
        }.bind(this));
    },
    comment() {
        WPapi.comment(this.pos, this.formc)
        .then(function( response ){
            console.log(response)
        }.bind(this));
    },
    deleteCo(id) {
        WPapi.deleteCo(id)
        .then(function( response ){
            console.log(response)
        }.bind(this));
    },
    editC(id) {
        this.showeditC = true;
        this.idc = id
    },
    submiteditC(id) {
        WPapi.editCo(id, this.formedit)
        .then(function( response ){
            console.log(response)
        }.bind(this));
        this.showeditC = false;
        this.idc = '';
        this.formedit= { content: ''};
    }
    }*/
}
</script>

<style scoped>
#back {
    display: flex;
    justify-content: center;
    position: fixed;
    top: 0;
    left: 0;
    width: calc(100% - 0px);
    min-height: calc(100vh - 0px);
}
.post{
     background-image: 
    linear-gradient(62deg,rgba(7,86,160) 13%, rgba(255,122,151) 4%),
    linear-gradient(44deg, rgba(0,43,99) 13%, rgba(242,140,143) 18%),
    linear-gradient(118deg, rgba(84,202,242) 40%, rgba(247,155,187) 54%),
    linear-gradient(58deg,rgba(90,90,237) 83%, rgba(249, 156, 142) 24%);
  width: 80%;
  max-height: 600px;
  padding: 10px;
  margin: 10px 0;
  border: 0.5px solid black;
  border-radius: 20px;
}
#btn{
margin: -5px 5px ;
margin-left: auto;
}
#com-space {
    height: 5px;
    width: 100%;
    margin: auto;
    background-color: rgb(87, 87, 87);
    border-radius: 5px;
}
#com {
    background: grey;
    margin: 0.5em;
    border-radius: 5px;
    color: rgb(224, 224, 224);
    padding: 5px;
}
#com a {
    color: ivory;
    cursor: pointer;
    text-decoration: underline;
}

#titleComm{
    margin-right: 5px;
    border-radius: 10px;
}
#bt1{
    border-radius: 10px;
}


</style>