<template>
  <div class="multi-selector">
    <label class="multi-selector__label">
      <span class="multi-selector__title">{{ title }}</span>
      <select v-model="selected" multiple class="multi-selector__input">
        <option v-for="option in options" v-bind:value="option" :key="option">
          {{ option }}
        </option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  name: "MultiSelectorField",
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
      type: Array,
      default: () => []
    }
  },
  computed: {
    selected: {
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
.multi-selector {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  text-align: left;
  padding: 1%;

  .multi-selector__label {
    display: flex;

    .multi-selector__title {
      width: 35%;
      min-width: 150px;
      font-size: 1.5rem;
    }

    .multi-selector__input {
      width: 63%;
      min-width: 150px;
      font-size: 1rem;
      height: 60px;
      text-align: center;
    }
  }
}
</style>
