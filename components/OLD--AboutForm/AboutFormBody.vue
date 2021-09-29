<template>
  <v-form id="about-form">
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
    <!-- //! <Icon icon="fe:arrow-down" color="#848484" width="25" height="25" /> -->

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
    <p>{{ about.residentCountry }}</p>
  </v-form>
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

//
// <v-form id="goals-radio">
//   <h2>what's it called?</h2>
//   <v-text-field v-model="form.title" label="name of form"> </v-text-field>
//   <h2>type</h2>

//   <v-radioGroup v-model="form.radioValue">
//     <v-radio label="contact" color="red" value="contact"> </v-radio>
//     <v-radio label="signup" color="yellow" value="signup"> </v-radio>
//     <v-radio label="donation" color="green" value="donation"> </v-radio>
//   </v-radioGroup>

//   <!-- <v-btn depressed elevation="3" outlined large>submit</v-btn> -->

//   <h2>{{ form.title }}: a {{ form.radioValue }} form</h2>
// </v-form>
</script>

<style scoped>
/* #about-form { */
/* //*moved margin to /pages/form.vue */
/* margin: 40px; */
/* border: 1px solid #ebebeb;
} */

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
</style>
