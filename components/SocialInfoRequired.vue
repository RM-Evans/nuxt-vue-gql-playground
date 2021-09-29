<template>
  <v-form>
    <h2>Main Account</h2>

    <div class="form-fields-container">
      <label>Social Platform<span>*</span></label>
      <input class="about-input" />
    </div>

    <div class="form-fields-container">
      <label>Username of URL<span>*</span></label>
      <input class="about-input" />
    </div>

    <div class="form-fields-container">
      <label>Current number of Followers<span>*</span></label>
      <input class="about-input" />
    </div>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      // model: {
      //   platform: '',
      //   username: '',
      //   followers: null,
      // },
      // props: {
      //   formData: Object,
      // },
    }
  },
}
</script>

<style scoped>
/* FORM STYLE START */

h2 {
  font-weight: normal;
  font-size: 18px;

  /* padding top is giving space between the individual forms */
  padding-top: 30px;
  padding-bottom: 2px;

  border-bottom: 2px solid #c44a42;

  text-align: center;
}

.form-fields-container {
  display: flex;
  flex-direction: column;

  width: 100%;

  margin-top: 30px;
}
.form-fields-container label {
  font-size: 16px;
  font-weight: 300;
  padding-left: 1px;
}
.form-fields-container span {
  color: #c44a42;
}
.about-input {
  border: 1px solid #848484;
  border-radius: 2px;

  height: 45px;

  padding: 5px 5px 5px 10px;
}
</style>
