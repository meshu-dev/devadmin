<template>
  <b-form method="post" @submit.prevent="submit">
    <h1>{{ pageTitle }}</h1>
    <b-form-group label-for="name-field" label-cols="2" label="Name:">
      <b-form-input
        id="name-field"
        v-model="fieldNameValue"
        type="text"
        required
      ></b-form-input>
    </b-form-group>
    <b-form-group label-for="url-field" label-cols="2" label="Url:">
      <b-form-input
        id="url-field"
        v-model="fieldUrlValue"
        type="url"
        required
      ></b-form-input>
    </b-form-group>
    <b-button type="submit" variant="primary">
      {{ btnText }}
    </b-button>
  </b-form>
</template>

<script>
export default {
  props: {
    pageTitle: {
      type: String,
      default: ''
    },
    btnText: {
      type: String,
      default: ''
    }
  },
  computed: {
    fieldNameValue: {
      get() {
        return this.$attrs['field-name-value']
      },
      set(val) {
        this.$emit('update:fieldNameValue', val)
      }
    },
    fieldUrlValue: {
      get() {
        return this.$attrs['field-url-value']
      },
      set(val) {
        this.$emit('update:fieldUrlValue', val)
      }
    }
  },
  methods: {
    submit() {
      this.$emit('form-submit')
    }
  }
}
</script>

<style scoped>
input {
  max-width: 300px;
}
</style>
