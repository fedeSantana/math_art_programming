/* eslint-disable no-console */
<template>
  <article>
    <h1>{{ chapter.title }}</h1>
    <p>{{ chapter.description }}</p>
    <img :src="chapter.img" />
    <nuxt-content :document="chapter" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const chapter = await $content('chapters', params.slug).fetch()
    return { chapter }
  },
}
</script>
