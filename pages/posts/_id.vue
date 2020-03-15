<template>
  <article>
    <h2>{{ title }}</h2>
    <p>{{ body }}</p>
    <nuxt-link to="/posts">Back</nuxt-link>
  </article>
</template>

<script>
import axios from 'axios'

export default {
  asyncData ({ params }) {
    return axios.get(`https://jsonplaceholder.typicode.com/posts/${params.id}`)
      .then(res => {
        return res.data
      })
  },

  head() {
    return {
      title: this.title
    }
  }
}
</script>