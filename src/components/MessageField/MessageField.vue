<template>
  <div class="msg-field">
    <div class="msg-field__row">
      <span class="msg-field__row__username">{{message.username}}</span>
      <span class="msg-field__row__date">{{message.date}}</span>
    </div>
    <div class="msg-field__text">{{message.text}}</div>
  </div>
</template>

<script>
export default {
  name: 'message-field',
  props: {
    message: Object
  },
  data: () => ({})
}
</script>

<style lang="scss" src="./main.scss"></style>
