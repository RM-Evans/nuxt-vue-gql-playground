<template>
  <div>
    <!-- step heading and info -->
    <div>
      <h1 class="stepTitle">Goals</h1>
      <h3 class="stepDescription">
        <span>Finally</span>, what are your goals how can we help you?
      </h3>
    </div>
    <!-- survey start -->
    <div class="questionAlign">
      <div class="question">
        <h2>How much time do you plan on committing to Everra?</h2>
        <v-radio-group v-model="model.timeCommitmentResponse">
          <v-radio label="Full-time (30+ hours weekly)" color="#c44a42" />
          <v-radio
            label="Part-time (less than 30 hours weekly)"
            color="#c44a42"
          />
        </v-radio-group>

        <div class="question">
          <h2>I want to make this a ___.</h2>
          <v-radio-group v-model="model.wantToMakeThisResponse">
            <v-radio label="Career" color="#c44a42" />
            <v-radio label="Hobby" color="#c44a42" />
          </v-radio-group>
        </div>

        <div class="question">
          <h2>How can we help you succeed in Everra?</h2>
          <v-radio-group v-model="model.howToSucceedResponse">
            <v-radio label="Dashboard Tools" color="#c44a42" />
            <v-radio label="Community Guidance" color="#c44a42" />
            <v-radio label="Social Media Guidance" color="#c44a42" />
          </v-radio-group>
        </div>
      </div>
    </div>

    <button
      @click="sendSurveyData"
      style="color: green; font-weight: bold; border: green 2px solid"
    >
      SEND RADIO DATA TO PARENT
    </button>

    <!-- nav buttons -->

    <div class="btn-container">
      <!-- back button -->
      <button class="back-btn-on-survey" @click="() => $emit('next', -1)">
        <p>back</p>
      </button>
      <!-- next button -->
      <button class="apply-btn-on-survey" @click="sendSurveyDataAndApply">
        <p>apply</p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      model: {
        timeCommitmentResponse: '',
        wantToMakeThisResponse: '',
        howToSucceedResponse: '',
      },
      //   filledRadioArray: [],
    }
  },
  props: {
    formData: Object,
  },
  methods: {
    sendSurveyData() {
      // let filledRadioModel = {
      //   timeCommitmentResponse: this.timeCommitmentResponse,
      //   wantToMakeThisResponse: this.wantToMakeThisResponse,
      //   howToSucceedResponse: this.howToSucceedResponse,
      // }

      this.$emit('submitSurvey', this.model)

      //   this.filledRadioArray.push(filledRadioModel)
    },
    sendSurveyDataAndApply() {
      const { formData } = this
      console.log({ formData })
      //send radio data to form.vue
      this.$emit('submitSurvey', this.model)
      // //TODO get all data from form.vue and SEND
      // this.$emit('formSubmitted', this.model)
      //go to next page
      this.$emit('next', 1)
    },
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
  padding: 20px 16px;
}
.stepDescription span {
  font-weight: bold;
}

/* HEADING END */

/* survey START */

.questionAlign {
  padding-left: 16px;
}

.question {
  margin-top: 20px;
}

.question h2 {
  font-size: 22px;
  padding-bottom: 10px;
}

.question >>> label {
  font-size: 18px;
  padding-bottom: 10px;
  /* align text with radio button */
  bottom: -5px;
}

/* survey END */

/* BUTTONS-START */

.btn-container {
  display: flex;
  justify-content: space-between;
  margin-top: 40px;
}
.apply-btn-on-survey,
.back-btn-on-survey {
  width: 130px;
  height: 50px;

  border-radius: 2px;
}

.apply-btn-on-survey {
  background-color: #c44a42;

  color: white;
  font-style: normal;
  font-weight: normal;
  font-size: 30px;
}

.back-btn-on-survey {
  background-color: white;
  border: 1px solid black;

  font-style: normal;
  font-weight: normal;
  font-size: 30px;
}

/* BUTTONS-END */
</style>
