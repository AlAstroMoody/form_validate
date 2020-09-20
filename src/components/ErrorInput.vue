<template>
  <span class="error">
    <i v-if="error === 'empty'">*обязательно для заполнения</i>
    <i v-if="error === 'alpha'">*только буквы</i>
    <i v-if="error === 'numeric'">*только цифры</i>
    <i v-if="error === 'phone'">*формат номера 7xxxxxxxxxx</i>
  </span>
</template>

<script>
export default {
  name: "ErrorInput",
  props: {
    error: {
      type: String,
      default: ""
    }
  }
};
</script>

<style scoped>
.error {
  color: red;
}
</style>
