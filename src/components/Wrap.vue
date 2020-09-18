<template>
  <div class="app">
    <div class="container">
      <Header :siteTitle="siteTitle"/>
      <main>
        <div class="page-content">
          <slot></slot>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
import variables from 'saber/variables'
import Header from './Header.vue'
import Footer from './Footer.vue'

export default {
  components: {
    Header,
    Footer
  },

  props: ['page'],

  head() {
    const { excerpt } = this.page
    const { title, layout } = this.page
    let { description } = this.$siteConfig
    if (layout === 'page' || layout === 'projects') {
      if (excerpt) {
        description = excerpt.replace(/<(?:.|\n)*?>/gm, '')
      }
    }
    return {
      title: title ? `${title} - ${this.siteTitle}` : this.siteTitle,
      meta: [
        description && {
          name: 'description',
          content: description
        }
      ].filter(Boolean)
    }
  },

  computed: {
    siteTitle() {
      return this.$siteConfig.title || 'Nonamed'
    }
  }
}
</script>
