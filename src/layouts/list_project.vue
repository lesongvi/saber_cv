<template>
  <Wrap :page="page">
    <div class="projects">

      <slot name="default"></slot>

      <div v-if="page.posts && page.posts.length > 0">
        <div class="project" v-for="post in page.posts" :key="post.permalink">
            <div class="project-name">{{ post.title }}</div>
            <div class="project-desc">{{ formatDate(post.createdAt) }}</div>
            <div class="project-links">
                <saber-link
                :to="post.permalink"
                ><svg xmlns="http://www.w3.org/2000/svg" width=".8em" height=".8em" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-link" data-v-0e387185=""><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71" data-v-0e387185=""></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71" data-v-0e387185=""></path></svg>
                Xem thêm</saber-link>
            </div>
        </div>
      </div>

      <div
        class="pagination"
        v-if="page.pagination && (page.pagination.hasNext || page.pagination.hasPrev)"
      >
        <router-link
          class="prev-link"
          :to="page.pagination.prevLink"
          v-if="page.pagination.hasPrev"
        >← Previous</router-link>
        <router-link
          class="next-link"
          :to="page.pagination.nextLink"
          v-if="page.pagination.hasNext"
        >Next →</router-link>
      </div>
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
