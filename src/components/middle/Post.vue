<template>
    <section>
        <div class="title">
            <h1>{{post.title}}</h1>
        </div>
        <div class="text">
            {{post.text}}
        </div>
        <h1>Comments: </h1>
        <ul>
            <Comment v-for="comment in getComments"
                     :comment="comment"
                     :users="users"/>
        </ul>
    </section>
</template>

<script>
    import Comment from './Comment';

    export default {
        name: 'Post',
        components: {
            Comment
        },
        props: ['users', 'post', 'comments'],
        beforeMount() {
            this.$root.$on('onChangePost', (post) => {
                this.post = post;
            });
        },
        computed: {
            getComments: function() {
                return Object.values(this.comments).filter(t => {
                    return t.postId === this.post.id;
                });
            }
        }
    };
</script>

<style scoped>
    .title {
        color: darkblue;
    }

    .text {
        line-height: 1.2;
        font-size: 1.5rem;
        font-family: "Roboto", sans-serif;
        margin: 0 0 5% 0;
    }
    ul{
        padding: 0;
    }
</style>
