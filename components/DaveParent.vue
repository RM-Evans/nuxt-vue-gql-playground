<template>
  <div>
    Parent! {{ step }}
    <DaveChild
      v-if="step == 1"
      @formData="onComplete"
      :parentForm="parentForm"
    />
    <DaveChild2
      v-if="step == 2"
      @back="step--"
      @formData="onComplete"
      :parentForm="parentForm"
    />
    <div v-if="step > 2">
      Your answers were:
      <pre><code> {{this.parentForm}} </code></pre>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      step: 1,
      parentForm: {},
    }
  },
  methods: {
    onComplete(formData) {
      console.log('Parent got it', formData)
      Object.assign(this.parentForm, formData)
      this.step++
    },
  },
}
</script>
