<template>
  <div class="input-form">
    <div class="input-form__wrap">
      <textarea
        :class="{'input-form__wrap__text': true, 'err': err}" rows="3"
        v-model="newMessage" @keyup.ctrl.enter="sendMessage()" @keydown="checkForm()"
        ></textarea>
      <p class="input-form__wrap__err" v-if="err">Поле не должно быть пустым</p>
    </div>
    <button type="submit" class="input-form__button" @click="sendMessage">
      Написать консультанту
    </button>
  </div>
</template>

<script>
export default {
  name: 'input-form',
  data: () => ({
    newMessage: '',
    err: false
  }),
  methods: {
    sendMessage () {
      if (!this.newMessage) {
        this.err = true
        return
      }
      if (this.err) {
        this.err = false
      }
      this.$emit('sendMessage', this.newMessage)
      this.newMessage = ''
    },
    checkForm () {
      if (this.newMessage !== undefined) {
        this.err = false
      }
    }
  }
}
</script>

<style lang="scss" src="./main.scss"></style>
