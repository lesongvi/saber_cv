<template>
  <Wrap :page="page">
    <div class="home">
      <slot name="default"></slot>
    </div>
  </Wrap>
</template>

<script>
import formatDate from '../utils/formatDate'
import Wrap from '../components/Wrap.vue'
export default {
  components: {
    Wrap
  },
  props: ['page'],
  computed: {
    feedLink() {
      return this.$feed && this.$feed.permalink
    }
  },
  methods: {
    formatDate
  }
}
</script>