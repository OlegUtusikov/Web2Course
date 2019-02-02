<template>
    <div class="UsersPageMain">
        <div class="header">
            <div>Id</div>
            <div>Login</div>
            <div>Name</div>
        </div>
        <UsersPageUser v-for="user in listUsers"
                       :user="user"/>
    </div>
</template>

<script>
    import UsersPageUser from './UsersPageUser';

    export default {
        name: 'UsersPage',
        components: {
            UsersPageUser
        },
        props: ['users'],
        computed: {
            listUsers: function() {
                return Object.values(this.users).sort((a, b) => {
                    return a.id - b.id;
                });
            }
        }

    };
</script>

<style scoped>
    .header {
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        margin: 0 0 25px 0;
        padding: 4px 0 4px 0;
        border-bottom: 3px solid cadetblue;
        background: #E1E1E1;
        border-radius: 5px;
        font-weight: 600;
    }

    .header > div {
        width: 29%;
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
    }
</style>
