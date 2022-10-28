<template>
  <div class="main-nav">
    <router-link :to="{name : 'home'}">Project</router-link>
    <router-link :to="{name : 'AddProject'}">Add a New Project</router-link>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.main-nav{
    text-align: center;
    margin: 40px auto;
}
.main-nav a{
    display: inline-block;
    text-decoration: none;
    margin: 0 10px;
    color: #999;
    font-size: 18px;
}
a.router-link-active{
    border-bottom: 2px solid #00ce98;
    padding-bottom: 4px; 
}

</style>