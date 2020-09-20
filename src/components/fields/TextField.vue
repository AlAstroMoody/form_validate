<template>
  <div class="text-field">
    <label class="text-field__label">
      <span class="text-field__title">{{ title }}</span>
      <input
        type="text"
        v-model="getValue"
        class="text-field__input"
        :maxlength="length"
      />
    </label>
  </div>
</template>

<script>
export default {
  name: "TextField",
  props: {
    title: {
      type: String,
      default: ""
    },
    value: {
      type: String,
      default: ""
    },
    length: {
      type: Number,
      default: 100
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
      width: 60%;
      min-width: 150px;
    }
  }
}
</style>
