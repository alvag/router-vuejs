<template>
    <div class="article">
        <Title text="Ruta con parámetros"/>
        <h2>Parámetro: {{ $route.params.id }}</h2>
        <h3>{{ article.title }}</h3>
        <p>{{ article.id }} - {{ article.body }}</p>
    </div>
</template>
<script>
import Title from '@/components/Title';

export default {
    name: 'Article',
    data() {
        return {
            article: {}
        };
    },
    created() {
        this.getArticle( this.$route.params.id );
    },
    components: {
        Title
    },
    methods: {
        async getArticle(id) {
            try {
                const response = await fetch( `https://jsonplaceholder.typicode.com/posts/${ id }` );
                this.article = await response.json();
            } catch ( e ) {
                console.log( e );
            }
        }
    }
};
</script>

<style scoped>

</style>
