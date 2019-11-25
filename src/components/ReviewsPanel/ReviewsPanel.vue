<template>
<div class="reviews-panel">
  <div class="reviews-panel__view-switch">
    <span :class="{ 'reviews-panel__view-switch__tab': true, 'active': !showAll }"
      @click="setShowAll(false)">Последние отзывы</span>
    <span :class="{ 'reviews-panel__view-switch__tab': true, 'active': showAll }"
      @click="setShowAll(true)">Все отзывы</span>
  </div>
  <div class="reviews-panel__statistics">
    <span class="reviews-panel__statistics__likes">{{likes}}</span>
    <span class="reviews-panel__statistics__comments">{{reviews}}</span>
  </div>
</div>
</template>

<script>
export default {
  name: 'reviews-panel',
  props: {
    likes: {
      type: Number,
      required: true
    },
    reviews: {
      type: Number,
      required: true
    }
  },
  data: () => ({
    showAll: false
  }),
  methods: {
    setShowAll (value) {
      if (this.showAll === value) {
        return
      }
      this.showAll = value
      this.$emit('showAll', value)
    }
  }
}
</script>

<style lang="scss" src="./main.scss"></style>
