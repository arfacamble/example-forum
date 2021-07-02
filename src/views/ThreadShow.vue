<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <PostList :postIds="postIds" />
    <form @submit.prevent="addPost">
      <div class="form-group">
        <textarea
          name=""
          id=""
          cols="30"
          rows="10"
          class="form-input"
          v-model="newPostText"
        ></textarea>
      </div>
      <div class="form-actions">
        <button class="btn-blue">Submit Post</button>
      </div>
    </form>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import PostList from '@/components/PostList'
  export default {
    props: {
      id: {
        required: true,
        type: String
      }
    },

    components: {
      PostList
    },

    computed: {
      postIds () {
        return Object.values(this.thread.posts)
      }
    },

    methods: {
      addPost () {
        const post = {
          text: this.newPostText,
          threadId: this.id,
          publishedAt: Math.floor(Date.now() / 1000),
          userId: '7uVPJS9GHoftN58Z2MXCYDqmNAh2'
        }
        const postId = `fakePostId${Math.floor(Math.random() * 10000000)}`
        this.$set(sourceData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourceData.users[post.userId].posts, postId, postId)
        this.newPostText = ''
      }
    },

    data () {
      return {
        thread: sourceData.threads[this.id],
        newPostText: ''
      }
    }
  }
</script>

<style scoped>
</style>
