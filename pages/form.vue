<template>
  <div class="form-and-btn-container">
    <!-- conditonally render based on which step im on -->
    <AboutForm v-show="step === 0" @next="(offset) => (step += offset)" />

    <SocialForm
      v-show="step === 1"
      :formData="DatabaseValues[step]"
      @next="handleNext"
      @formSubmitted="handleFormSubmit"
    />

    <SurveyForm
      v-show="step === 2"
      @next="(offset) => (step += offset)"
      :formData="DatabaseValues[step]"
      @filledForm="handleFilledForm"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      step: 0,
      DatabaseValues: {
        //need to get form comp data
        socialData: [
          {
            // formData: Object,
            platform: String,
            username: String,
            followers: Number,
          },
        ],
        radioData: {
          formData: Object,
          //whatever my prop is called on the component element above?
        },
      },
    }
  },
  methods: {
    handleNext(offset, formData) {
      //check for validation -- if valid then allow @next
      this.step += offset
    },
    handleFormSubmit(filled) {
      // Send to graphql possibly
      // Add to local array, etc.
      //*I can see all the data i pass from my components from data() in form.vue
      console.log(filled)
    },
    handleFilledForm(formData) {
      console.log(
        // `social: ${filled.socialData[1]} | radio: ${filled.radioData} `
        { formData }
      )

      // console.log(
      //   `about: ${filled.aboutData} | social: ${filled.socialData} | radio: ${filled.radioData} `
      // )
    },
  },
}
</script>

<style scoped>
.form-and-btn-container {
  margin: 40px;
}
</style>
