<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        netlifynuxtcms
      </h1>
      <h2 class="subtitle">
        My tremendous Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
      <h2 v-html="post.html"></h2>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
   async asyncData({ params }) {
      try {
        let post = await import(`~/_posts/blog/2019-08-26-starting.md`);
        console.log(post, 'test')
        return { post: post.default }
      } catch(err) {
        console.debug(err)
        return false
      }
    },
  components: {
    Logo
  },

  mounted: function () {
    console.log('test')
  }
}




</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
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

.links {
  padding-top: 15px;
}
</style>
