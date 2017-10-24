<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title">
        Terra JS
      </h1>
      <h2 class="subtitle">
        Open Source Collective making modules for Node.js and Vue.js
      </h2>
      <div class="links">
        <a href="https://github.com/terrajs" target="_blank" class="button--grey">GitHub</a>
        <a href="https://twitter.com/terra_js" target="_blank" class="button--grey">Twitter</a>
      </div>
      <h3 class="repos-title">
        Projects
      </h3>
      <div class="repos">
        <div class="repo" v-for="repo in repos" :key="repo.id">
          <a :href="repo.html_url" target="_blank" class="repo-title">
            {{ repo.name }}
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  async asyncData({ app }) {
    const { data } = await app.$axios.get('https://api.github.com/orgs/terrajs/repos')

    return {
      repos: data
    }
  },
  components: {
    Logo
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Roboto", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 700;
  font-size: 80px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.repos-title {
  font-weight: 300;
  font-size: 32px;
  color: #526488;
  word-spacing: 5px;
  margin-bottom: 30px;
}

.repo {
  padding: 5px 0;
}

.repo-title {
  text-transform: capitalize;
  font-weight: bold;
  text-decoration: none;
  color: #526488;
}

.repo-title:hover {
  text-decoration: underline;
}

.links {
  padding-top: 15px;
  margin-bottom: 100px;
}
</style>
