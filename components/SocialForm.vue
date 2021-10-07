<template>
  <!-- or I could just put the Main form title on here, give it a required asterisk. 
Then make all these forms come from a singular component, while pushing to an array of Accounts.
as long as I make sure the 0 and 1 are always rendered. 0 = main, 1 = secondary.  
0 must be fully completed for validation.
 0 and 1 will need different titles than any extra form that is rendered
 need to keep track of each form

 if i add an extra, then im adding another form to the array. if there is nothing in that form, then dont send

main should be completed to go to next step

 
 socialForm: [
  {
    name: 'main',
    fields: {
      platform: {
        text: "Platform",
        required: true
      },
      username: '',
      followers: #
    }
   },
   secondary: {
     platform: ''
     username: ''
     followers: #
   },
   extras: [{
     extraOne:{
     platform: ''
     username: ''
     followers: #
     },
     extraTwo:{
     platform: ''
     username: ''
     followers: #
     }
     
   }]

   }]



   I should be using Form.vue as the controller. it should manage the state of each step in the form. the children (eg: socialForm[i]() which would be each form in the array)
   -->
  <div>
    <!-- step heading and info -->
    <div>
      <h1 class="stepTitle">social</h1>
      <h3 class="stepDescription">
        <span>Second</span>, where are you posting on social media?
      </h3>
    </div>

    <SocialInfoRequired />
    <SocialInfoSecondary />
    <!-- //TODO: work out a good way to pass each form to parent 
    also, try pushing each form to an array and display it to the page in json
    -->
    <input class="testInput" v-model="model.social.platform" />
    <input class="testInput" v-model="model.social.username" />
    <input class="testInput" v-model="model.social.followers" />

    <button
      @click="sendData"
      style="color: green; font-weight: bold; border: green 2px solid"
    >
      SEND MODEL DATA TO PARENT
    </button>
    <div v-show="toggleExtraFields"><SocialInfoExtra /></div>

    <div class="add-fields-container">
      <p>add another account</p>
      <div @click="showExtraFields">
        <!-- //!!! icon PRODUCES ERROR  $attrs is readonly && $attrs is readonly-->
        <div style="border: solid 30px green; width: 55px; height: 55px"></div>
        <!-- <Icon
          :icon="icons.addCircle24Filled"
          width="55px"
          height="55px"
          color="#5B5B5B"
        /> -->
      </div>

      <!-- 
      <div v-for="form in formArray">
        <SocialFormComponent></SocialFormComponent>
      </div> -->

      <!-- //! referenced during render :(
        <button @click="addExtraFields">just button lol</button>

      <component
        v-for="(extraField, index) in extraFields"
        :key="index"
        :is="extraField"
      /> -->
    </div>

    <!-- nav buttons -->

    <div class="btn-container">
      <!-- back button -->
      <button class="back-btn-on-social" @click="() => $emit('next', -1)">
        <p>back</p>
      </button>
      <!-- next button -->
      <button class="next-btn-on-social" @click="sendDataAndProceed">
        <p>next</p>
      </button>
    </div>
  </div>
</template>

<script>
import { Icon } from '@iconify/vue2/dist/offline'
//* MUST USE CommonJs package format https://docs.iconify.design/icon-components/vue2/offline.html#:~:text=CommonJS%20package%3A%20%40iconify/icons-%7Bprefix%7D
import addCircle24Filled from '@iconify/icons-fluent/add-circle-24-filled'

const extraField = {
  template: '<SocialInfoExtra />',
}

export default {
  components: {
    Icon,
  },
  props: {
    formData: Array,
  },
  data() {
    return {
      model: {
        social: {
          platform: '',
          username: '',
          followers: null,
        },
      },
      // socialArray: [],  //! I should handle this on parent?
      icons: {
        addCircle24Filled,
      },

      toggleExtraFields: false,
    }
  },
  methods: {
    showExtraFields() {
      this.toggleExtraFields = !this.toggleExtraFields
    },

    sendData() {
      //*testing purposes
      this.$emit('socialSubmit', this.model.social)
    },

    sendDataAndProceed() {
      //TODO want to send
      this.$emit('socialSubmit', this.model.social)
      this.$emit('next', 1)
    },

    //!!!formData doesnt exist here. im expecting it to be all the data ive collected in form.vue???? am passing formData Object as a prop, above
    // pushToArray() {
    //   //* collect form state, push to array, update form.vue

    //   let socialFormData = {
    //     platform: this.model.social.platform,
    //     username: this.model.social.username,
    //     followers: this.model.social.followers,
    //   }
    //   this.socialArray.push(socialFormData)
    // },
  },
}
</script>

<style scoped>
.testInput {
  border: 1px grey solid;
  margin: 5px 0;
}

.add svg {
  width: 46px;
}
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

/* FORM STYLE END */

/* faded text and add button START */

.add-fields-container {
  display: flex;
  flex-direction: column;

  margin-top: 30px;

  /* border: red solid 2px; */
}
/*//! p element MARGIN is being overwritten with .v-application -- is margin: 16px*/
.add-fields-container p,
.add-fields-container div {
  margin: 5px;
  font-size: 20px;
  align-self: center;
  color: #5b5b5b;
  /* border: blue solid 2px; */
}

/* faded text and add button END */

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
}

.back-btn-on-social {
  background-color: white;
  border: 1px solid black;

  font-style: normal;
  font-weight: normal;
  font-size: 30px;
}

/* BUTTONS-END */
</style>
