/* eslint-disable no-console */
<template>
  <div>
    {{ slug }}
    <article v-if="chapter">
      <h1>{{ chapter.title }}</h1>
      <p>{{ chapter.description }}</p>
    </article>
    <pre v-if="files">{{ files }}</pre>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const content = await $content('chapters', params.slug, {
      deep: true,
    }).fetch()

    if (Array.isArray(content)) {
      const files = JSON.stringify(content, null, 2)
      return { files, slug: params.slug }
    }

    return { chapter: content, slug: params.slug }
  },
}
</script>
