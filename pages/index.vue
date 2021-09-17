<template>
  <div class="container">
    <NuxtLogo />
    <h1 class="title">nuxt-mission</h1>
    <p v-if="$fetchState.pending">Fetching planets ...</p>
    <p v-else-if="$fetchState.error">Error while fetching planets ...</p>
    <ul>
      <li v-for="planet in planets" :key="planet.slug">
        <NuxtLink :to="planet.slug">{{ planet.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      planets: []
    }
  },
  async fetch() {
    this.planets = await fetch(
      'https://api.nuxtjs.dev/planets'
    ).then((res) => res.json())
  }
}
</script>

<style scoped>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
font-size: 100px;
color: #020a46;
font-family: arial, sans-serif;
font-weight: 600;
}

.link {
  margin: auto;
  font-size: 30px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li a{
 text-decoration: none;
 font-size: 40px;
 color: #020a46;
}
li a:hover{
 color: #0ac297;
}
</style>
