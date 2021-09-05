<template>
  <div class="container">
    <NuxtLogo />
    <h1 class="title">nuxt-mission</h1>
    <NuxtLink to="/about" class="link">About</NuxtLink>
    <p v-if="$fetchState.pending">Fetching planets ...</p>
    <p v-else-if="$fetchState.error">Error while fetching planets ...</p>
    <ul>
      <li>
        <NuxtLink to="/nuxt">Nuxt</NuxtLink>
      </li>
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
font-size: 80px;
}

.link {
  margin: auto;
  font-size: 30px;
}

ul {
  list-style-type: none;
  padding: 0;
}
</style>
