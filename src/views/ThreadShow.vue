<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <PostList :postIds="postIds" />
    <PostEditor @save-post="savePost" :threadId="id"/>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import PostList from '@/components/PostList'
  import PostEditor from '@/components/PostEditor'
  export default {
    props: {
      id: {
        required: true,
        type: String
      }
    },

    components: {
      PostList,
      PostEditor
    },

    computed: {
      postIds () {
        return Object.values(this.thread.posts)
      }
    },

    data () {
      return {
        thread: sourceData.threads[this.id],
      }
    },

    methods: {
      savePost (event) {
        const post = event.post
        const postId = post['.key']
        this.$set(sourceData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourceData.users[post.userId].posts, postId, postId)
      }
    }
  }
</script>

<style scoped>
</style>
