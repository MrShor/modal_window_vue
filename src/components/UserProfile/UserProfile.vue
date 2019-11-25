<template>
  <div class="user-profile">
    <div class="user-profile__title">
      <p class="user-profile__title__user-name">{{userProfile.name}}</p>
      <p class="user-profile__title__user-position">{{userProfile.position}}</p>
    </div>
    <div class="user-profile__photo-wrap">
      <img
        class="user-profile__photo-wrap__img"
        src="@/assets/img/user-photo.jpg" alt="user-photo"
      >
      <div class="user-profile__photo-wrap__description">{{userProfile.description}}</div>
    </div>
    <div class="user-profile__statistics">
      <p class="user-profile__statistics__title">Услуг</p>
      <div class="user-profile__statistics__graph">
        <div
          class="user-profile__statistics__graph__row"
          v-for="(item, index) in userProfile.graphs" :key="index"
        >
          <span
            class="background-line"
            :class="сhangeLineColor(item.value)"
          >
            <span class="background-line__text">
              {{item.category}}
            </span>
          </span>
          <span class="value">{{item.value}}</span>
        </div>
      </div>
      <div class="user-profile__statistics__total">
        <span>Всего</span>
        <span>{{userProfile.totalValue}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'user-profile',
  props: {
    userProfile: Object
  },
  methods: {
    сhangeLineColor (value) {
      if (value >= 10) {
        return `green width-10`
      }
      if (value < 10) {
        return `blue width-${value}`
      }
    }
  }
}
</script>

<style lang="scss" src="./main.scss"></style>
