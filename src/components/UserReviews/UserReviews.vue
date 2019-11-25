<template>
  <div class="user-reviews">
    <message-feild v-for="(item, index) in messages" :key="index" :message="item"></message-feild>
  </div>
</template>

<script>
import MessageFeild from '../MessageField/MessageField.vue'

export default {
  name: 'user-reviews',
  props: {
    messages: Array
  },
  components: {
    MessageFeild
  }
}
</script>
