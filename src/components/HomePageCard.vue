<template>
     <v-card
        min-height="450"
        dark
        class="box"
        v-customScroll="handleScroll"
    >
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="headline">{{ title }} #{{ index }}</v-list-item-title>
                <v-card-text class="body-1">{{ text }}</v-card-text>
            </v-list-item-content>
        </v-list-item>
    </v-card>
</template>

<script>
export default {
  name: 'HomePageCard',
  props: {
    text: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    index: {
      type: Number,
      default: 1
    },
    length: {
      type: Number,
      default: 0
    }
  },
  methods: {
    handleScroll: function (evt, el) {
      const { top, bottom } = el.getBoundingClientRect()
      if (top > 159 && bottom < 849) {
        el.classList.add('box-active')
      } else {
        el.classList.remove('box-active')
      }
      if (this.index === 1) {
        if (window.scrollY < 50) {
          el.classList.remove('box-active')
        }
      }
    }
  }
}
</script>
<style lang="sass" scoped>
.box
  opacity: 0
  transform: translateZ(0)
  perspective: 1000px
  backface-visibility: hidden
  transition: 1.5s all cubic-bezier(0.39, 0.575, 0.565, 1)
.box-active
  opacity: 1
  transform: translate3d(0, -10px, 0)
</style>
