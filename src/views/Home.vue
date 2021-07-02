<template>
  <div class='col-full'>
    <h1>The Forum: People Talk</h1>
    <ThreadList :threads="threads"/>
  </div>
</template>

<script>
import sourceData from '../data'
import ThreadList from '../components/ThreadList'
export default {
  components: {
    ThreadList
  },

  data() {
    return {
      threads: Object.values(sourceData.threads),
      posts: sourceData.posts,
      users: sourceData.users
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
