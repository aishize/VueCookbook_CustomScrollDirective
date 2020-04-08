<template>
    <v-container>
        <v-row class="d-flex justify-center">
            <v-col lg="6" sm="8" md="8" cols="10" v-scroll="scrollHandler">
                <div class="inform">
                    <p
                        class="display-1 text-inform-up"
                        v-customScroll.once="handleScrollUp"
                    >
                        scroll down
                    </p>
                </div>
                <card
                    v-for="(text, title, index) in texts"
                    :key="'card-' + index"
                    :text="text"
                    :title="title"
                    :index="index + 1"
                    :length="textsLength"
                    class="my-10"
                />
                <div class="inform">
                    <p
                        class="display-1 text-inform-down"
                        v-customScroll="handleScrollDown"
                    >
                        scroll up
                    </p>
                </div>
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
import texts from '@/utils/LoremIpsumText'
import HomePageCard from '../components/HomePageCard'

export default {
  name: 'HomePage',
  components: {
    card: HomePageCard
  },
  data: () => ({
    texts
  }),
  computed: {
    textsLength: function () {
      return Object.keys(this.texts).length
    }
  },
  methods: {
    handleScrollUp: function (evt, el) {
      if (window.scrollY > 50) {
        el.classList.add('text-inform-up-active')
      } else {
        el.classList.remove('text-inform-up-active')
      }
    },
    handleScrollDown: function (evt, el) {
      const bottom = Math.floor(window.scrollY / this.textsLength)
      if (bottom === 445) {
        el.classList.add('text-inform-down-active')
      } else {
        el.classList.remove('text-inform-down-active')
      }
    }
  }
}
</script>
<style lang="sass" scoped>
.lorem-text
  font-size: 20pt
.inform
  display: flex
  height: 250px
  align-items: center
  justify-content: center
  color: #FFFFFF
.text-inform-up
  opacity: 1
  transition: .8s all cubic-bezier(0.39, 0.575, 0.565, 1)
.text-inform-down
  opacity: 0
  transition: .8s all cubic-bezier(0.39, 0.575, 0.565, 1)
.text-inform-up-active
  opacity: 0
  transform: translate3d(0, -10px, 0)
.text-inform-down-active
  opacity: 1
  transform: translate3d(0, -10px, 0)
</style>
