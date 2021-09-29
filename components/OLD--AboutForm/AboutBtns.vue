<template>
  <div class="btn-container">
    <button class="next-btn-on-about" @click="() => $emit('next', 1)">
      <p>next</p>
    </button>
  </div>
</template>

<script>
export default {
  methods: {},
}
</script>

<style scoped>
/* BUTTONS-START */

.about-btn-container {
  display: flex;
  justify-content: flex-end;
}
.next-btn-on-about {
  width: 130px;
  height: 50px;
  background-color: #c44a42;
  border-radius: 2px;
}
.next-btn-on-about {
  font-style: normal;
  font-weight: bold;
  font-size: 30px;

  color: white;
}

/* BUTTONS-END */
</style>
