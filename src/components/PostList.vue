<template>
  <div class="post-list">
    <PostListItem
      v-for="postId in postIds"
      :key="postId"
      :post="findPost(postId)"
    />
  </div>
</template>

<script>
  import sourceData from '@/data'
  import PostListItem from './PostListItem'
  export default {
    props: {
      postIds: {
        required: true,
        type: Array
      }
    },
    components: {
      PostListItem
    },
    methods: {
      findPost: function (postId) {
        return sourceData.posts[postId]
      }
    }
  }
</script>
