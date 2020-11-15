<template>
  <div>
      <input v-model="input" v-on:keyup="(event) => this.$emit('inputChange', input)" :placeholder=placeholder>
  </div>
</template>

<script>
export default {
  name: 'ValueInput',
  props: {
    placeholder: String,
  },
  data () {
      return {
          input: ''
      }
  }
}
</script>