<template>
  <div class="btn-container">
    <!-- back button -->
    <button class="back-btn-on-social" @click="() => $emit('next', -1)">
      <p>back</p>
    </button>
    <!-- next button -->
    <button class="next-btn-on-social" @click="() => $emit('next', 1)">
      <p>next</p>
    </button>
  </div>
</template>

<style scoped>
/* BUTTONS-START */

.btn-container {
  display: flex;
  justify-content: space-between;
  margin-top: 40px;
}
.next-btn-on-social,
.back-btn-on-social {
  width: 130px;
  height: 50px;

  border-radius: 2px;
}

.next-btn-on-social {
  background-color: #c44a42;

  color: white;
  font-style: normal;
  font-weight: normal;
  font-size: 30px;
  /* line-height: 36px; */
}

/* .next-btn-on-social {
  font-style: normal;
  font-weight: bold;
  font-size: 30px;
  line-height: 36px;
} */

.back-btn-on-social {
  background-color: white;
  border: 1px solid black;

  font-style: normal;
  font-weight: normal;
  font-size: 30px;
  /* line-height: 36px; */
}

/* BUTTONS-END */
</style>
