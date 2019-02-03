<template>
  <li>
    <div class="title">By: {{users[comment.userId].login}}</div>
    <div class="text">{{comment.text}}</div>
  </li>
</template>

<script>
  export default {
    name: 'Comment',
    props: ['comment', 'users']
  };
</script>

<style scoped>
  li{
    list-style: none;
    margin: 0 0 3% 0;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0;
    font-family: "Roboto", sans-serif;
  }
  .title {
    margin: 0 0 1% 0;
    font-size: 1.3rem;
    color: gray;
    text-decoration: underline;
  }
  .text{
    line-height: 1.2;
  }
</style>
