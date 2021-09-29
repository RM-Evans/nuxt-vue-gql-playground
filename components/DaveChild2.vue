<template>
  <div>
    Child2! <br />
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
    parentForm: Object,
  },
  data() {
    return {
      something: '',
    }
  },
  methods: {
    sendForm() {
      const { something } = this
      const payload = { something }
      this.$emit('formData', payload)
    },
  },
}
</script>
