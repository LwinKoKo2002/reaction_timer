<template>
  <p>Reaction time - {{ score }}</p>
  <div v-if="score <= 250">
    <p>Omg! you are god of catching.</p>
  </div>
  <div v-else-if="score > 250 && score < 500">
    <p>Nice catching man.</p>
  </div>
  <div v-else>
    <p>Slow man! catch me fast.</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
};
</script>

<style scoped>
p {
  color: #2c3e50;
}
</style>