
<template>
  <div class="home" >
    <FilterNav @filter="filter" :current="current" :projects="projects"/>
    <div v-if="projects.length">
      <div v-for="project in filteredProjects" :key="project.id" >
          <SingleProject v-if="current" :project="project" @delete="handleDelete" @complete="handleComplete"/>
      </div>
    </div>
   
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject'
import FilterNav from '../components/FilterNav'

export default {
  name: 'Home',
  components: { SingleProject, FilterNav },
  data() {
    return {
      projects: [],
      current: 'all',
      //filteredProjects: []
    }
  },
  mounted() {
    fetch('http://localhost:3000/projects')
      .then(res => res.json())
      .then(data => {
        this.projects = data
        this.filteredProjects = this.projects.filter(project => {
          return project.completed = true || false
        })
        })
      .catch(err => console.log(err.message))
    
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => {
        return project.id !== id
      })
    },
    handleComplete(id) {
      let p = this.projects.find(project => {
        return project.id === id
      })
      p.complete = !p.complete
    },
    filter(e) {
      this.current = e
      // switch(e) {
      //   case 'all':
      //     console.log('all', this.projects);
      //     this.filteredProjects = this.projects.filter(project => {
      //         return project
      //     })
      //     break
      //   case 'completed':
      //     this.filteredProjects = this.projects.filter(project => {
      //         return project.complete === true
      //     })
      //     break
      //   case 'ongoing':
      //     this.filteredProjects = this.projects.filter(project => {
      //         return project.complete === false
      //     })
      //     break
      // }
    }
  },
  computed: {
    filteredProjects() {
      if (this.current === 'completed') {
        return this.projects.filter(project => project.complete)
      }
      if (this.current === 'ongoing') {
        return this.projects.filter(project => !project.complete)
      }
      return this.projects
    }
  }
}

//  All we're doing is grabbing the data in the mounted hook, updating the projects, then when we have
//  the project, were looping through them and outputting the title for each one.

</script>
