<template>
  <div class="container mt-5">
    <div class="card">
      <div class="card-body my-2 " v-for="articulo in articulos" :key="articulo.id">
          <nuxt-link :to="`blog/${ articulo.id }`">
            <h1 class="text-blue">{{ articulo.title }}</h1>
          </nuxt-link>
        <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ad, nam molestiae consequatur recusandae ea modi nemo quam in expedita, eaque temporibus deserunt, doloremque officia? Laudantium nam tenetur nulla officia quis!</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data(){
    return{
      articulos: []
    }
  },
  async created(){
    const res = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
    //console.log(res.data);
    this.articulos = res.data;
  }

}
</script>
