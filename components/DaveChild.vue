<template>
  <div>
    Child!
    <v-radio-group v-model="radioOption">
      <v-radio label="Full-time (30+ hours weekly)" color="#c44a42" />
      <v-radio label="Part-time (less than 30 hours weekly)" color="#c44a42" />
    </v-radio-group>
    <v-text-field v-model="textValue" />
    <br />
    <button @click="sendForm">Send</button>
  </div>
</template>

<script>
export default {
  props: {
    parentForm: Object,
  },
  watch: {
    parentForm: {
      deep: true, // hes a big old object with nested objects / arrays
      immediate: true, // do it when we first load
      handler(newVal, oldVal) {
        console.log(
          'this state',
          newVal,
          oldVal,
          this.radioOption,
          this.textValue
        )
        this.radioOption = newVal.radioOption
        this.textValue = newVal.textValue
      },
    },
  },
  data() {
    return {
      radioOption: null,
      textValue: '',
    }
  },
  methods: {
    sendForm() {
      const { radioOption, textValue } = this
      const payload = { radioOption, textValue }
      console.log('child has', payload)
      this.$emit('formData', payload)
    },
  },
}
</script>
