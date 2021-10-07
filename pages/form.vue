<template>
  <div class="form-and-btn-container">
    <!-- conditonally render based on which step im on -->
    <AboutForm
      v-show="step === 0"
      :formData="DatabaseValues"
      @next="handleNext"
      @aboutSubmit="handleSubmitAbout"
    />

    <SocialForm
      v-show="step === 1"
      :formData="DatabaseValues.social"
      @next="handleNext"
      @socialSubmit="handleSubmitSocial"
    />

    <!-- <SurveyForm
      v-show="step === 2"
      @next="(offset) => (step += offset)"
      :formData="DatabaseValues[step]"
      @filledForm="handleFilledForm"
    /> -->

    <SurveyForm
      v-show="step === 2"
      :formData="DatabaseValues.survey"
      @next="(offset) => (step += offset)"
      @submitSurvey="handleSubmitSurvey"
    />

    <ApplicationProcessing
      v-show="step === 3"
      :DatabaseValues="DatabaseValues"
    />

    <!-- {{ DatabaseValues }} -->
    <p>about</p>
    {{ DatabaseValues.about }}
    <br />
    <br />
    <p>social</p>
    {{ DatabaseValues.social }}
    <br />
    <br />
    <p>survey</p>
    {{ DatabaseValues.survey }}
    <br />
    <br />

    <a @click="() => this.step--">go back</a>
    <br />
  </div>
</template>

<script>
export default {
  data() {
    return {
      step: 0,
      DatabaseValues: {
        about: {},
        social: [],
        survey: {},
      },
    }
  },
  methods: {
    handleNext(offset, formData) {
      //check for validation -- if valid then allow @next
      this.step += offset
    },

    handleSubmitAbout(formData) {
      // console.log({ DatabaseValues: JSON.stringify(this.DatabaseValues) })
      Object.assign(this.DatabaseValues.about, formData)
      console.log('Parent got about', { formData })
    },
    handleSubmitSocial(data) {
      //* push to social:[]
      console.log({ data })
      this.DatabaseValues.social.push({ ...data })
    },

    handleSubmitSurvey(formData) {
      Object.assign(this.DatabaseValues.survey, formData)
      console.log('Parent got survey', { formData })
    },

    // // handleFormSubmit(filled) {
    // //   // Send to graphql possibly
    // //   // Add to local array, etc.
    // //   //*I can see all the data i pass from my components from data() in form.vue
    // //   console.log(filled)
    // // },
    // // handleArray(formData) {
    // //   console.log({ formData })
    // //   Object.assign(this.DatabaseValues.social, {
    // //     ...this.DatabaseValues.social,
    // //     formData,
    // //   })
    // // },

    // handleFilledForm(formData) {
    //   console.log({ DatabaseValues: JSON.stringify(this.DatabaseValues) })
    //   Object.assign(this.DatabaseValues, formData)
    //   console.log('Parent got it', { formData })
    // },
  },
}
</script>

<style scoped>
.form-and-btn-container {
  margin: 40px;
}
</style>
