<template>
  <nav class="nav">
      <h1>
        <saber-link class="site-title" to="/">{{ siteTitle }}</saber-link>
      </h1>
      <ul class="menu">
        <li>
          <saber-link to="/projects.html">Dự án</saber-link>
        </li>
        <li>
          <saber-link to="/me.html">Hồ sơ</saber-link>
        </li>
      </ul>
  </nav>
</template>

<script>
export default {
  props: {
    siteTitle: {
      type: String,
      required: true
    }
  }
}
</script>
