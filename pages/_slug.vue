<template>
  <div class="container">
    <img :src="planet.image" alt="" class="planet">
    <h1>{{ planet.title }}</h1>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const planet = await fetch(
      `https://api.nuxtjs.dev/planets/${params.slug}`
    ).then((res) => {
      if(res.ok) {
        return res.json()
      }
      throw new Error(res.status)
    })
    return { planet }
  }
}
</script>

<style scoped>
.container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

h1 {
  font-family: arial, sans-serif;
  font-weight: normal;
  font-size: 5em;
}

.link {
  margin: auto;
  font-size: 50px;
}

.planet {
  width: 20%;
  margin-top: 40px;
  align-items: center;
  justify-content: center;
}
</style>
