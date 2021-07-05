<template>
  <span :title="humanFriendlyDate">
    {{humanFriendlyTimeAgo}}
  </span>
</template>

<script>
  import moment from 'moment'
  export default {
    props: {
      timestamp: {
        required: true,
        type: Number
      }
    },

    computed: {
      humanFriendlyTimeAgo () {
        return moment.unix(this.timestamp).fromNow()
      },
      humanFriendlyDate () {
        return moment.unix(this.timestamp).format('MMMM Do YYYY, h:mm:ss a')
      }
    }
  }
</script>
