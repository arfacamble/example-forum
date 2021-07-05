<template>
  <div class="post">
    <div class="user-info">
      <a href="#" class="user-name">{{user.name}}</a>
      <a href="#">
        <img :src="user.avatar" alt="" class="avatar-large">
      </a>
      <p class="desktop-only text-small">{{postsCount}} posts</p>
    </div>

    <div class="post-content">
      <div>
        <p>
          {{post.text}}
        </p>
      </div>
    </div>

    <div class="post-date text-faded">
      <AppDate :timestamp="this.post.publishedAt" />
    </div>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import AppDate from './AppDate'
  export default {
    props: {
      post: {
        required: true,
        type: Object
      }
    },

    components: {
      AppDate
    },

    computed: {
      user () {
        return sourceData.users[this.post.userId]
      },
      postsCount () {
        return Object.keys(this.user.posts).length
      }
    }
  }
</script>
