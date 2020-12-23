<template>
  <nav class="filter-nav">
      <button :class="{active: current === 'all'}" @click="updateFilter('all')">View All</button>
      <button @click="updateFilter('completed')" :class="{ active: current === 'completed' }">Completed</button>
      <button @click="updateFilter('ongoing')" :class="{ active: current === 'ongoing' }">Ongoing</button>
  </nav>
</template>

<script>
export default {
    props: [ 'current', 'projects'],
    data() {
        return {
            
        }
    },
    methods: {
        updateFilter(by) {
            this.$emit('filter', by)
            // console.log(this.filter);
            
        },
       
    },
    mounted() {
        // console.log(this.projects);
    }
    
}
</script>

<style>
    .filter-nav button {
        background: none;
        border: none;
        color: #bbb;
        outline: none;
        font-size: 12px;
        text-transform: uppercase;
        margin-right: 10px;
        font-weight: bold;
        cursor: pointer;
    }
    .filter-nav button.active{
        color: #555;
    }
</style>