<template>
  <section>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h1 class="mb-5">Presents for your Pair!</h1>
        </div>
        <div class="col-12 text-center">
          <h2 class="mb-4">Roses</h2>
        </div>
        <div v-for="i in 22" :key="i" class="col-12 col-md-4 col-lg-4">
          <img
            class="w-100 mb-3"
            :src="require(`~/assets/img/${i}.JPG`)"
            alt=""
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {}
  },
  methods: {},
}
</script>

<style scoped>
.content {
  margin: 0 auto;
  max-width: 768px;
}

.sidebar {
  min-width: 300px;
}
</style>
