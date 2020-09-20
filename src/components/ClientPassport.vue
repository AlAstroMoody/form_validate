<template>
  <div>
    <h2>Паспортные данные</h2>
    <selector-field
      title="Тип документа"
      :options="['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение']"
      :value.sync="passport.documentType"
    />
    <error-input error="empty" v-if="!$v.passport.documentType.required" />
    <text-field title="Серия" :value.sync="passport.series" />
    <text-field title="Номер" :value.sync="passport.ID" />
    <text-field title="Кем выдан" :value.sync="passport.organization" />
    <date-field title="Дата выдачи" :value.sync="passport.dateOfIssue" />
    <error-input error="empty" v-if="!$v.passport.dateOfIssue.required" />
  </div>
</template>

<script>
import SelectorField from "@/components/fields/SelectorField";
import TextField from "@/components/fields/TextField";
import DateField from "@/components/fields/DateField";
import { required, numeric } from "vuelidate/lib/validators";
import ErrorInput from "@/components/ErrorInput";

export default {
  name: "ClientPassport",
  props: {
    passport: {
      type: Object,
      default: () => {}
    }
  },
  components: { ErrorInput, DateField, TextField, SelectorField },
  validations: {
    passport: {
      documentType: {
        required
      },
      series: {
        numeric
      },
      ID: {
        numeric
      },
      dateOfIssue: {
        required
      }
    }
  },
  updated() {
    this.passport.valid = !this.$v.passport.$invalid;
  }
};
</script>

<style scoped></style>
