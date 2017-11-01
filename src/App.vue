<template>
    <div class="corpo">
        <h1 class="centralizado">{{titulo}}</h1>
        <ul class="lista-fotos">
            <li class="lista-fotos-itens" v-for="foto of fotos">
                <img :src="foto.url" :alt="foto.titulo">
            </li>
        </ul>
    </div>
</template>
<script>


export default {
    data(){
        return{
            titulo: 'alurapic',
            fotos:[
            ]
        }
    },
    created(){
        this.$http.get('http://localhost:3000/v1/fotos')
     .then(res => res.json())
     .then(fotos => this.fotos = fotos, err => console.log(err));
 }
}
</script>

<style>
.corpo{
    font-family: verdana;
    width: 96%;
    margin: 0 auto;
}
.centralizado{
    text-align: center;
}
.lista-fotos{
    list-style: none;
}
.lista-fotos .lista-fotos-itens{
    display: inline-block;
}
</style>
