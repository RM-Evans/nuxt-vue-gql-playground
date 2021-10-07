<template>
  <div>
    Child2! <br />
    <!-- parentForm is the prop im passing in --- allows me to use all the data from each component
    because I have been collecting those objects in DaveParent.vue -->
    You said you work {{ parentForm.radioOption }} hours! <br />

    <v-text-field v-model="something" label="Do you like your hours?" />

    <br />
    <button @click="$emit('back')">Back</button>
    <button @click="sendForm">Next</button>
  </div>
</template>

<script>
export default {
  props: {
    //passing props here so that I can see the parent object and render it in this components HTML
    parentForm: Object,
  },
  // watch: {
  //   //* works if I change @formData="onComplete"  to @formData="onCompleteGoBack" --- using onCompleteGoBack test function in DaveParent.vue
  //   //am using this in order to remember state in case I need to go back to this step --  so I can go back and change if I made a mistake
  //   //! I need to send payload to parent before this can work like its supposed to
  //   parentForm: {
  //     deep: true, // hes a big old object with nested objects / arrays
  //     immediate: true, // do it when we first load
  //     handler(newVal, oldVal) {
  //       console.log('dave2 state', newVal, oldVal, this.something)
  //       this.something = newVal.something
  //     },
  //   },
  // },
  data() {
    return {
      //refer to v-model="something"
      something: '',
    }
  },
  methods: {
    sendForm() {
      const { something } = this
      const payload = { something }
      //am telling parent that this child has the user input
      this.$emit('formData', payload) //@formData="onComplete"  on DaveParent.vue is where I see this
    },
  },
}

//!emitting on next button so thats why the watcher isnt seeing the data and saving it
</script>
