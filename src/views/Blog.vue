<template>
    <div class="blog">
        <Title text="Mi Blog"/>

        <ul>
            <li v-for="item in articles" :key="item.id">
                <router-link :to="`/blog/${item.id}`">{{ item.title }}</router-link>
            </li>
        </ul>
    </div>
</template>

<script>

import Title from '@/components/Title';

export default {
    name: 'Blog',
    components: { Title },
    data() {
        return {
            articles: []
        };
    },
    created() {
        this.getArticles();
    },
    methods: {
        async getArticles() {
            try {
                const response = await fetch( 'https://jsonplaceholder.typicode.com/posts' );
                this.articles = await response.json();
            } catch ( e ) {
                console.log( e );
            }
        }
    },

};
</script>

<style scoped>

</style>
