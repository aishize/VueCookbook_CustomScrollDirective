<template>
    <v-container>
        <v-row class="d-flex justify-center">
            <v-col lg="6" sm="8" md="8" cols="10">
                <v-card
                    v-for="(text, title, index) in texts"
                    :key="index"
                    min-height="350"
                    class="my-10"
                >
                    <v-list-item>
                        <v-list-item-content>
                            <v-list-item-title class="headline">{{ title }} #{{ index + 1 }}</v-list-item-title>
                            <v-card-text class="body-1">{{ text }}</v-card-text>
                        </v-list-item-content>
                    </v-list-item>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
import texts from '@/utils/LoremIpsumText'

export default {
  name: 'HomePage',
  data: () => ({
    texts
  }),
  computed: {}
}
</script>
<style lang="sass" scoped>
.lorem-text
  font-size: 20pt
</style>
