<template>
  <div>
    <docs :page="page" />

    <!-- <div v-if="latestThemes.length > 0" class="bg-orange-100 py-16">
      <div class="container mx-auto">
        <h2 id="build" class="text-3xl text-center font-semibold text-gray-900 mb-4">
          Latest community Themes
        </h2>
        <div class="grid md:grid-cols-3 gap-4">
          <t-card
            v-for="theme in latestThemes"
            :key="theme.id"
            header="Bootstrap"
            variant="theme"
          >
            <p>{{ theme.description }}</p>
            <template v-slot:header>
              <span class="px-3">{{ theme.name }}</span>
              <t-button variant="link" :to="`/themes/${theme.slug}`">
                Preview →
              </t-button>
            </template>
          </t-card>
        </div>
      </div>
    </div> -->
  </div>
</template>

<script>
import Vue from 'vue'
import Docs from '~/components/Docs.vue'

export default Vue.extend({
  components: {
    Docs
  },
  async asyncData ({ $content }) {
    const page = await $content('home').fetch()

    return {
      page
    }
  },
  data () {
    return {
      latestThemes: []
    }
  },
  created () {
    this.$axios.get('/themes')
      .then(({ data }) => {
        this.latestThemes = data.data
      })
  }
})
</script>
