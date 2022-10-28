<script>
import SinglePage from '../components/SinglePage.vue';
import FilterNav from '../components/FilterNav.vue';
export default {
  name:"home",
  components: { SinglePage , FilterNav },

  data() {
    return {
      projects: [],
      current:'all'
    };
  },
  mounted() {
    fetch(" http://localhost:3000/project")
      .then((res) => res.json())
      .then((data) => (this.projects = data))
      .catch((err) => console.log(err.message));
  },
  methods:{
    handleDelete(id){
      this.projects = this.projects.filter(item=> {
        return item.id != id
      })
    },
    handleComplet(id){
      let p = this.projects.find(item =>{
        return item.id === id
      })
      p.complete = !p.complete
    }
  },
  computed:{
    filteredProjects(){
      if (this.current === 'Copmleted') {
        return this.projects.filter(item => item.complete)
      }else if (this.current === 'Ongoing') {
        return this.projects.filter(item => !item.complete)
      }else{
        return this.projects
      }
    }
  }
};
</script>

<template>
  
  <FilterNav @filterChange="current = $event" :current="current"/>
  <div v-if="projects.length">
    <div v-for="project in filteredProjects" :key="project.id">
    <SinglePage  :project="project" @delete="handleDelete" @complet="handleComplet"/>
    </div>
  </div>
</template>


<style>
</style>
