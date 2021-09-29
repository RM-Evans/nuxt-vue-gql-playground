<template>
  <div>
    <!-- step heading and info -->
    <div>
      <h1 class="stepTitle">About</h1>
      <h3 class="stepDescription">
        <span>First</span>, we’d like to know a little bit about yourself.
      </h3>
    </div>

    <v-form id="form-parent">
      <!-- first name -->
      <div class="form-fields-container">
        <label>First name</label>
        <input v-model="about.firstName" class="about-input" />
      </div>
      <!-- last name -->
      <div class="form-fields-container">
        <label>Last name</label>
        <input v-model="about.lastName" class="about-input" />
      </div>
      <!-- email -->
      <div class="form-fields-container">
        <label>Email</label>
        <input v-model="about.email" class="about-input" />
      </div>
      <!-- phone number -->
      <div class="form-fields-container">
        <label>Phone number</label>
        <input v-model="about.phoneNumber" class="about-input" />
      </div>
      <!-- country of residence -->

      <!-- //TODO figure out iconify with nuxt (dropdown arrow)
    //*https://docs.iconify.design/types/iconify-json.html
    //*https://docs.iconify.design/icon-components/vue/
    //*https://icon-sets.iconify.design/fe/arrow-down/ -->

      <div class="form-fields-container">
        <label>Country of residence</label>
        <select
          v-model="about.residentCountry"
          class="about-input"
          id="tempSelectARROW"
        >
          <option disabled value="">select one</option>
          <option>USA</option>
          <option>NZ</option>
          <option>AU</option>
        </select>
      </div>
    </v-form>

    <!-- nav buttons -->

    <div class="about-btn-container">
      <button class="next-btn" @click="() => $emit('next', 1)">
        <p>next</p>
      </button>
    </div>
  </div>
</template>

<script>
//! import { Icon } from '@iconify/vue'
export default {
  data() {
    return {
      about: {
        firstName: '',
      },
      form: {
        title: '',
        radioValue: '',
      },
    }
  },
}
</script>

<style scoped>
/* HEADING START */

.stepTitle {
  font-size: 36px;
  text-align: center;
}
.stepDescription {
  font-size: 20px;
  font-weight: 300;
  padding: 20px 20px;
}
.stepDescription span {
  font-weight: bold;
}
/* HEADING END */

/* FORM STYLE START */
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
.about-input {
  border: 1px solid #848484;
  border-radius: 2px;

  height: 45px;

  padding: 5px 5px 5px 10px;
}

/* //! TEMPORARY */
#tempSelectARROW {
  -webkit-appearance: menulist !important; /* override vuetify style */
  -moze-appearance: menulist !important; /* override vuetify style */
  appearance: menulist !important; /* override vuetify style */
}

/* FORM STYLE END */

/* BUTTONS-START */

.about-btn-container {
  display: flex;
  justify-content: flex-end;
  margin-top: 40px;
}

.next-btn,
.back-btn {
  width: 130px;
  height: 50px;

  border-radius: 2px;
}

.next-btn {
  background-color: #c44a42;

  color: white;
  font-style: normal;
  font-weight: normal;
  font-size: 30px;
}

.back-btn {
  background-color: white;
  border: 1px solid black;

  font-style: normal;
  font-weight: normal;
  font-size: 30px;
}

/* BUTTONS-END */
</style>
