<template>
  <div>
    <h2>Адрес</h2>
    <text-field title="Индекс" :value.sync="address.index" :length="6" />
    <error-input error="numeric" v-if="!$v.address.index.numeric" />

    <text-field title="Страна" :value.sync="address.country" />
    <error-input error="alpha" v-if="!$v.address.country.alpha" />

    <text-field title="Область" :value.sync="address.region" />
    <error-input error="alpha" v-if="!$v.address.region.alpha" />

    <text-field title="Город" :value.sync="address.city" />
    <error-input error="empty" v-if="!$v.address.city.required" />
    <error-input error="alpha" v-if="!$v.address.city.alpha" />

    <text-field title="Улица" :value.sync="address.street" />
    <text-field title="Дом" :value.sync="address.house" />
  </div>
</template>

<script>
import TextField from "@/components/fields/TextField";
import { required, numeric } from "vuelidate/lib/validators";

import ErrorInput from "@/components/ErrorInput";

export default {
  name: "ClientAddress",
  props: {
    address: {
      type: Object,
      default: () => {}
    }
  },
  components: { ErrorInput, TextField },
  validations: {
    address: {
      country: {
        alpha: val => /^[а-яё]*$/i.test(val)
      },
      index: {
        numeric,
      },
      region: {
        alpha: val => /^[а-яё]*$/i.test(val)
      },
      city: {
        required,
        alpha: val => /^[а-яё]*$/i.test(val)
      }
    }
  },
  updated() {
    this.address.valid = !this.$v.address.$invalid;
  }
};
</script>

<style scoped></style>
