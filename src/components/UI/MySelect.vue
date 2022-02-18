<template>
  <select v-model="modelValue" @change="chacgeOption">
    <option disabled value="">Выбрать из списка</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "MySelect",
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    },
    methods: {
      chacgeOption(event) {
        this.$emit('update:modelValue', event.target)
      }
    }
  }
}
</script>

<style scoped>

</style>