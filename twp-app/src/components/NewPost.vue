<template>
        <div>
            <ul>
                <li v-for="(post,index) in posts" :key="post.id">{{post.title}}&nbsp;&nbsp;&nbsp;<button id="bt2" @click="openEdit(post.id)">🖊️</button><span v-if="showedit"></span>&nbsp;&nbsp;&nbsp;<button id="bt3" @click="removePost(index)">🗑️</button><span></span></li>
            </ul>
            <edit-post v-if="showedit" :idedit='idedit' :post="posts[idedit].title" @closePost="closePost"/>
        </div>
        <div id="creator">
            <input id="titlePost" v-model="posttitle" placeholder="Entrer un nouveau Post">
            <button id="bt1" @click="addPost">Ajouter un Post</button>
        </div> 
</template>

<script>

import EditPost from "./ShowPost.vue"
export default {
    name:'CreatePost',
    components:{EditPost},
    data() {
        return {
          posts : [],
              counter:1,
              idedit: '',
              showedit: false,
        }
        
    },
    methods: {
        addPost(){
            this.posts.push({title:this.posttitle,id:this.counter++})    
        },
        openEdit(id) {
            if (this.showedit === true) {
                this.showedit = false;
            }
            else {
                this.showedit = true;
                this.idedit = id-1;
            }
            console.log(this.idedit)
         },
        removePost(index){
           
            this.posts.splice(index,1)
        },
        closePost() {
     this.post = '';
     this.showedit = false;
    }
    } 
}
</script>

<style>

#creator{
    display:flex;
    justify-content: space-between;
}

li {
    width: 100%;
    display: block;
    justify-content: center center;
    padding-bottom : 10px;
    border-radius: 10px;
    margin-top: 10px;
}


#titlePost{
    margin-right: 5px;
    border-radius: 10px;
}
#bt1{
    border-radius: 10px;
}
@media (max-width: 640px){
  #listCat{
    width: 300%;
  }
  #creator{
    width: 300%;
  }
  #titlePost{
    width: 70%;
  }
}
</style>