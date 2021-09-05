<template>
  <div class="container">
    <NuxtLogo />
    <NuxtLink to="/about" class="link">About</NuxtLink>
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
  margin: 0;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  text-align: center;
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
