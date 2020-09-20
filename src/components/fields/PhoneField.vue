<template>
  <div class="data-field">
    <label class="data-field__label">
      <span class="data-field__title">{{ title }}</span>
      <input
        type="tel"
        v-model="getValue"
        class="data-field__input"
        maxlength="11"
        placeholder="7xxxxxxxxxx"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "PhoneField",
  props: {
    title: {
      type: String,
      default: ""
    }
  },
  value: {
    type: String,
    default: ""
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
.data-field {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  text-align: left;
  padding: 1%;

  .data-field__label {
    display: flex;
    height: 30px;

    .data-field__title {
      width: 35%;
      min-width: 150px;
      font-size: 1.5rem;
    }

    .data-field__input {
      width: 60%;
      min-width: 150px;
      text-align: center;
    }
  }
}
</style>
