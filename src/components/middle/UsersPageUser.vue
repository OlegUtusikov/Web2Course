<template>
    <div class="UsersPageUserMain">
        <div class="id">{{this.user.id}}</div>
        <div class="login">{{this.user.login}}</div>
        <div class="name">{{this.user.name}}</div>
    </div>
</template>

<script>
    export default {
        name: 'UsersPageUser',
        props: ['user']
    };
</script>

<style scoped>
    .UsersPageUserMain {
        display: flex;
        flex-direction: row;
        width: 100%;
        justify-content: space-around;
        margin: 0 0 10px 0;
        padding: 5px 0 5px 0;
        border: 1px solid #3B5998;
        border-radius: 5px;
        background: cornsilk;
    }

    .UsersPageUserMain > div {
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        width: 29%;
    }
</style>
