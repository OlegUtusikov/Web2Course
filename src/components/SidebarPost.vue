<template>
    <section>
        <div class="header">
            By {{users[post.userId].login}}
        </div>
        <div class="body">
            {{post.text}}
        </div>
        <div class="footer">
            <a href="#"
               @click="changePage('Post')">View all</a>
        </div>
    </section>

</template>

<script>
    export default {
        name: 'SidebarPost',
        props: ['users', 'post'],
        methods: {
            changePage: function(page) {
                this.$root.$emit('onChangePage', page);
                this.$root.$emit('onChangePost', this.post);
            }
        }
    };
</script>

<style scoped>

</style>
