<template>
    <div class="container">
        <div class="card">
            <div class="card-body">
                <h1>{{ articulo.title }}</h1>
                <p class="small">{{ autor.name }}</p>
                <p>{{ articulo.body }}</p>
                <nuxt-link to="/blog" class="btn btn-primary" >
                    Atrás
                </nuxt-link>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
        }
    },
    // async created(){
        
    // },
    async asyncData({params}){
        const res = await axios.get(`https://jsonplaceholder.typicode.com/posts/${ params.id }`);
        const articulo = res.data;

        const res2 = await axios.get(`https://jsonplaceholder.typicode.com/users/${ articulo.userId }`)
        const autor = res2.data;

        return{
            articulo,
            autor
        }
    }
}
</script>