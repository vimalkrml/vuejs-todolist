<script>
export default {};
</script>

<template>
  <div class="bg-gray-200 hero h-72 rounded">
    <div class="header">
      <h1 class="text-3xl font-bold text-gray-600">No tasks Found</h1>
      <h2 class="text-xl font-bold text-gray-600 mb-5">
        Please add some tasks.
      </h2>
      <button
        class="
          px-4
          pb-1
          text-xl text-white
          bg-gray-400
          hover:bg-black
          rounded-md
          mb-5
        "
      >
        +
      </button>
    </div>
  </div>
</template>

<style scoped>
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero > .header {
  padding: 20px;
  text-align: center;
}
.hero > .header > p {
  padding: 10px;
}
</style>