<template>
  <div>
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
  export default {
    props: {
      threadId: {
        required: true,
        type: String
      }
    },

    data () {
      return {
        newPostText: ''
      }
    },

    methods: {
      addPost () {
        const postId = `fakePostId${Math.floor(Math.random() * 10000000)}`
        const post = {
          '.key': postId,
          text: this.newPostText,
          threadId: this.threadId,
          publishedAt: Math.floor(Date.now() / 1000),
          userId: '7uVPJS9GHoftN58Z2MXCYDqmNAh2'
        }
        this.newPostText = ''

        this.$emit('save-post', { post })
      }
    }
  }
</script>
