<template>
  <div>
    <div class="thread">
      <p>
        <router-link :to="{name: 'ThreadShow', params: { id: id }}">
          {{thread.title}}
        </router-link>
      </p>
      <p class="text-faded text-xsmall">
        By <a href="#">{{user.name}}</a>, {{thread.publishedAt}}.
      </p>
    </div>
    <div class="activity">
      <p class="replies-count">
        {{repliesCount}} replies
      </p>
      <!-- <img src="#" alt="" class="avatar-medium"> -->

    <!-- <div>
      <p class="text-xsmall">
        <a href="#"></a>
      </p>
    </div> -->
    </div>
  </div>
</template>

<script>
  import sourceData from '@/data'
  export default {
    name: 'ThreadListItem',
    props: {
      thread: {
        required: true,
        type: Object
      }
    },
    computed: {
      id () {
        return sourceData.posts[this.thread.firstPostId].threadId
      },
      repliesCount () {
        return Object.keys(this.thread.posts).length - 1
      },
      user () {
        return sourceData.users[this.thread.userId]
      }
    }
  }
</script>
