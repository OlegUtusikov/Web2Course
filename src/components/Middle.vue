<template>
    <div class="middle">
        <Sidebar :posts="posts"
                 :users="users"></Sidebar>
        <main>
            <Index v-if="page === 'Index'"
                   :posts="posts"
                   :users="users"/>
            <Enter v-if="page === 'Enter'"/>
            <Register v-if="page === 'Register'"/>
            <AddPost v-if="page === 'AddPost'"/>
            <EditPost v-if="page === 'EditPost'"/>
            <UsersPage v-if="page === 'UsersPage'"
                       :users="users"/>
            <Post v-if="page === 'Post'"
                  :users="users" :post="curPost" :comments="comments"/>
        </main>
    </div>
</template>
<script>
    import Index from './middle/Index';
    import Enter from './middle/Enter';
    import Register from './middle/Register';
    import AddPost from './middle/AddPost';
    import EditPost from './middle/EditPost';
    import UsersPage from './middle/UsersPage';
    import Sidebar from './Sidebar';
    import Post from './middle/Post';

    export default {
        name: 'Middle',
        components: {
            Post,
            EditPost,
            Index,
            Enter,
            Register,
            AddPost,
            Sidebar,
            UsersPage
        },
        props: ['users', 'posts', 'comments'],
        data: function() {
            return {
                page: 'Index',
                curPost: ""
            };
        }, mounted() {
            this.$root.$on('onChangePage', (page) => {
                this.page = page;
            });
            this.$root.$on("onChangePost", (post) => {
                this.curPost = post;
            });
        }
    };
</script>

<style scoped>

</style>
