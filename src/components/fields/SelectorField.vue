<template>
  <div class="text-field">
    <label class="text-field__label">
      <span class="text-field__title">{{ title }}</span>
      <select v-model="getValue" class="text-field__input">
        <option v-for="option in options" :value="option" :key="option">
          {{ option }}
        </option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  name: "SelectorField",
  props: {
    options: {
      type: Array,
      default: () => []
    },
    title: {
      type: String,
      default: ""
    },
    value: {
      type: String,
      default: ""
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
.text-field {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  text-align: left;
  padding: 1%;

  .text-field__label {
    display: flex;

    .text-field__title {
      width: 35%;
      min-width: 150px;
      font-size: 1.5rem;
    }

    .text-field__input {
      width: 63%;
      min-width: 150px;
      font-size: 1rem;
      height: 30px;
      text-align: center;
    }
  }
}
</style>
