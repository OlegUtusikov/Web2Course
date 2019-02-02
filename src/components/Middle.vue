<template>
    <div class="middle">
        <Sidebar :posts="posts"
                 :users="users"></Sidebar>
        <main>
            <Index v-if="page === 'Index'"/>
            <Enter v-if="page === 'Enter'"/>
            <Register v-if="page === 'Register'"/>
            <AddPost v-if="page === 'AddPost'"/>
            <EditPost v-if="page === 'EditPost'"/>
            <UsersPage v-if="page === 'UsersPage'"
                       :users="users"/>
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

    export default {
        name: 'Middle',
        components: {
            EditPost,
            Index,
            Enter,
            Register,
            AddPost,
            Sidebar,
            UsersPage
        },
        props: ['users', 'posts'],
        data: function() {
            return {
                page: 'Index'
            };
        }, beforeCreate() {
            this.$root.$on('onChangePage', (page) => {
                this.page = page;
            });
        }
    };
</script>

<style scoped>

</style>
