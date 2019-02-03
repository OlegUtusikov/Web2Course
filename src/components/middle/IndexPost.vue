<template>
    <section>
        <div class="header"
             @click="changePage('Post')">{{post.title}}
        </div>
        <div class="body">{{post.text}}</div>
        <div class="footer">
            By {{users[post.userId].login}}
        </div>
    </section>
</template>

<script>
    export default {
        name: 'IndexPost',
        props: ['users', 'post'],
        methods: {
            changePage: function(page) {
                this.$root.$emit('onChangePost', this.post);
                this.$root.$emit('onChangePage', page);
            }
        }
    };
</script>

<style scoped>
    section {
        width: 90%;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        margin: 0 0 6% 0;
        position: relative;
        line-height: 1;
    }

    section > div {
        margin: 0 0 0 3%;
    }

    section::before {
        content: "";
        height: 100%;
        border-left: 5px solid #3B5998;
        position: absolute;
    }

    section > .header {
        color: darkblue;
        font-size: 1.5rem;
        margin: 0 0 1% 3%;
        cursor: pointer;
    }

    section > .body {
        line-height: 1.4;
        font-family: "Roboto", sans-serif;
        margin: 0 0 2% 3%;
    }

    section > .footer {
        font-size: 1.2rem;
        color: darkgray;
    }
</style>
