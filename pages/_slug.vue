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
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.link {
  margin: auto;
  font-size: 30px;
}

.planet {
  width: 10%;
  margin-top: 40px;
}
</style>
