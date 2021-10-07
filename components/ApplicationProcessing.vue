<template>
  <div>
    <h1>Your application is being processed!</h1>
    <h2>
      You will recieve an email at <span>{{ DatabaseValues.about.email }}</span>
    </h2>

    <br />
  </div>
</template>

<script>
export default {
  props: {
    DatabaseValues: Object,
    //props essentially creates properties on the "this" context
  },
}
</script>
<style scoped>
h1 {
  font-size: 36px;
  text-align: center;
}

h2 {
  font-size: 20px;
  font-weight: 300;
  padding: 20px 16px;
}
</style>
