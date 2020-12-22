<template>
  <div class="home">
    Home
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {},
  data() {
    return {

    }
  },
  mounted() {
    fetch('http://localhost:3000/projects')
      .then(res => res.json())
      .then(data => {})
  }
}
</script>
