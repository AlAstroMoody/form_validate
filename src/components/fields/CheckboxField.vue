<template>
  <div class="checkbox-field">
    <label class="checkbox-field__label">
      <input type="checkbox" v-model="getValue" class="checkbox-field__input" />
      <span class="checkbox-field__title">{{ title }}</span>
    </label>
  </div>
</template>

<script>
export default {
  name: "CheckboxField",
  props: {
    title: {
      type: String,
      default: ""
    },
    value: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    getValue: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("update:value", value);
      }
    }
  }
};
</script>

<style scoped lang="scss">
.checkbox-field {
  display: flex;
  text-align: left;
  padding: 1%;

  .checkbox-field__label {
    .checkbox-field__title {
      width: 35%;
      min-width: 150px;
      font-size: 1rem;
    }
  }
}
</style>
