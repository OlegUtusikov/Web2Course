<template>
    <aside>
        <SidebarPost v-for="post in viewPosts"
                     :post="post"
                     :users="users"/>
    </aside>
</template>

<script>
    import SidebarPost from './SidebarPost';

    export default {
        name: "Sidebar",
        components: {
            SidebarPost
        },
        props: ['users', 'posts'],
        computed: {
            viewPosts: function () {
                return Object.values(this.posts).sort((a, b) => b.id - a.id).slice(0, 4);
            }
        }
    }

</script>

<style scoped>

</style>
