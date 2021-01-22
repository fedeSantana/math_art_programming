<template>
  <article>
    <nuxt-content :document="chapter" />
    <h1>{{ chapter.title }}</h1>
    <p>{{ chapter.description }}</p>
    <img :src="chapter.img">
  </article>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const chapter = await $content('chapters', params.slug).fetch()

    return { chapter }
  }
}
</script>
