<template>
  <section>
    <div>User: {{name}}, his age is {{age}}</div>
  </section>
</template>

<script>
export default {
  name: 'UserName',
  data() {
    return {
      name: 'Hena',
      age: 33,
    };
  },
};
</script>

<style scoped lang="scss">
div {
  font-size: 42px;
  color: darkgreen;
}
</style>
