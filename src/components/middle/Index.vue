<template>
    <div class="main">
        <IndexPost v-for="post in posts" :users="users" :post="post"/>
    </div>
</template>

<script>
    import IndexPost from "./IndexPost";
    export default {
        name: "Index",
        components : {
          IndexPost
        },
      props: ["users", "posts"]
    }
</script>

<style scoped>

</style>
