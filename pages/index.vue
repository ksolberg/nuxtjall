<template>
  <div>
    <h1>{{ content.heading }}</h1>
    <router-link to="/about">about</router-link>
    {{ name }}
  </div>
</template>

<script>

export default {
  async asyncData ({ app, req }) {

    const res = await app.$umbraco.query('/root/home', 'XPath').getAll();

    const content = (res && res.totalResults == 1)
            ? res.results[0]
            : null;

    return {
      name: req ? 'server' : 'client',
      content
    }
  }
}
</script>

