<template>
    <section class="categorie">
        <div id="headerCat">
            <input id="titleCat" v-model="text" placeholder="Entrer une nouvelle Categorie">
            <span @click="$emit('remove')" id="closeCat">❌</span>
        </div>
        <div>
            <create-Post/>
        </div>
    </section>
</template>
<script>

import CreatePost from './NewPost.vue'

export default {
    name: 'CategorieComp',
    components :{CreatePost},

}

</script>

<style>


.categorie {
    height : auto;
    width : 20%;
    background-color: rgba(255,255,255,0.3);
    display : flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding : 1%;
    border-radius: 20px;
    margin:0.5% 1%;
}

#headerCat{
    display: flex;
    justify-content: flex-end;
    width: 100%;
}

#titleCat{
    width: 90%;
    border-radius: 10px;
}


#closeCat{
margin-left: 2.5%;
cursor: pointer;
}


</style>