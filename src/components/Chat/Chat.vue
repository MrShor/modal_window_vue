<template>
  <div class="chat">
    <user-profile :userProfile="userProfile"></user-profile>
    <reviews-panel
      :likes="123" :reviews="messages.length"
      @showAll="changeMessages"
    >
    </reviews-panel>
    <user-reviews :messages="messagesShowed"></user-reviews>
    <input-form @sendMessage="sendMessage"></input-form>
  </div>
</template>

<script>
import UserProfile from '../UserProfile/UserProfile.vue'
import ReviewsPanel from '../ReviewsPanel/ReviewsPanel.vue'
import UserReviews from '../UserReviews/UserReviews.vue'
import InputForm from '../InputForm/InputForm.vue'

export default {
  name: 'chat',
  data: () => ({
    showAllMsg: false,
    defaultShowed: 3,
    currentShowed: 0,
    messages: [
      {
        username: 'Самуил',
        date: '13 октября 2011',
        text: 'Самуил  13 октября 2011 Привет, Верунь! ниче себе ты крутая. фотка класс!!!!'
      },
      {
        username: 'Лилия Семёновна',
        date: '14 октября 2011',
        text: 'Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент, это и есть всемирно известный центр огранки алмазов и торговли бриллиантами?'
      },
      {
        username: 'Лилия Семёновна',
        date: '14 октября 2011',
        text: 'Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?'
      }
    ],
    userProfile: {
      name: 'Вероника Ростова',
      position: 'Менеджер по продажам',
      description: 'Подберу для вас самые лучшие предложения. Мои услуги абсолютно бесплатны.',
      graphs: [
        {
          category: 'Ручное бронирование',
          value: 11
        },
        {
          category: 'Пакетные туры',
          value: 3
        },
        {
          category: 'Отели',
          value: 1
        }
      ],
      totalValue: 15
    },
    newMessage: ''
  }),
  methods: {
    sendMessage (msg) {
      let date = new Date().toLocaleString('ru-Ru', {
        day: 'numeric',
        month: 'long',
        year: 'numeric'
      })
      this.messages.push({
        username: 'Лилия Семёновна',
        date: date.split('г.')[0],
        text: msg
      })
      if (this.showAllMsg) {
        this.currentShowed = this.messages.length
      } else {
        this.currentShowed = this.defaultShowed
      }
    },
    changeMessages (showAll) {
      if (showAll) {
        this.currentShowed = this.messages.length
        this.showAllMsg = true
      } else {
        this.currentShowed = this.defaultShowed
        this.showAllMsg = false
      }
    }
  },
  computed: {
    messagesShowed () {
      return this.messages.slice(this.messages.length - this.currentShowed)
    }
  },
  created () {
    this.currentShowed = this.defaultShowed
  },
  components: {
    UserProfile,
    ReviewsPanel,
    UserReviews,
    InputForm
  }
}
</script>

<style lang="scss" src="./main.scss"></style>
