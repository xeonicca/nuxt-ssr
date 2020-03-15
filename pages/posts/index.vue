<template>
  <article>
    <h2>{{ title }}</h2>
    <ul v-for="post in posts">
      <li><nuxt-link :to="{ name: 'posts-id', params: { id: post.id }}">{{ post.title }}</nuxt-link></li>
    </ul>
  </article>
</template>

<script>
import axios from 'axios'

export default {
  asyncData ({ params }) {
    return axios.get(`https://jsonplaceholder.typicode.com/posts`)
      .then(res => {
        return {
          posts: res.data
        }
      })
  }
}
</script>