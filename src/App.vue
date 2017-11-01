<!-- alurapic/src/App.vue -->

<template>
  <div class="corpo">

    <h1 class="titulo">{{ titulo }}</h1>

    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto in fotos">

          <painel :titulo="foto.titulo">
              <img class="imagem-responsiva" :src="foto.url" :alt="foto.titulo">
          </painel>

      </li>
    </ul>

  </div>
</template>

<script>
import Painel from './components/Painel.vue';
export default {
    components:{
        'painel' :Painel
        //, 'outros-elementos: elementos'
    },
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

  .titulo {
    text-align: center;
  }

  .corpo {
    font-family: Helvetica, sans-serif;
    margin: 0 auto;
    width: 96%;
  }

  .lista-fotos {
    list-style: none;
  }

  .lista-fotos .lista-fotos-item {
    display: inline-block;
  }

  .imagem-responsiva {
    width: 100%;
  }
</style>
