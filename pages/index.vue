<template>
  <div>

  </div>
</template>

<script>

export default {
  layout: 'index'
}
</script>

<style scoped>



  .container {
    display: grid;
    grid-gap: 5px;
    grid-template-columns: repeat(auto-fit, minmax(1500, 1fr));
    grid-template-rows: repeat(2, 900px);
  }
  .container > div > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    margin: 0;
    padding: 0;
  }
</style>