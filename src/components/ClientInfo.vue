<template>
  <div class="client-info">
    <h2>Основная информация</h2>
    <text-field title="Фамилия" :value.sync="client.surname" />
    <error-input error="empty" v-if="!$v.client.surname.required" />
    <error-input error="alpha" v-if="!$v.client.surname.alpha" />

    <text-field title="Имя" :value.sync="client.name" />
    <error-input error="empty" v-if="!$v.client.name.required" />
    <error-input error="alpha" v-if="!$v.client.name.alpha" />

    <text-field title="Отчество" :value.sync="client.patronymic" />
    <error-input error="alpha" v-if="!$v.client.patronymic.alpha" />

    <date-field title="Дата рождения" :value.sync="client.birthday" />
    <error-input error="empty" v-if="!$v.client.birthday.required" />

    <phone-field title="Телефон" :value.sync="client.phone" />
    <error-input error="empty" v-if="!$v.client.phone.required" />
    <error-input error="numeric" v-if="!$v.client.phone.numeric" />
    <error-input error="phone" v-if="!$v.client.phone.phone" />

    <div class="client-info__gender">
      <label>
        <input type="radio" value="male" v-model="client.gender" />
        Мужчина
      </label>
      <label>
        <input type="radio" value="female" v-model="client.gender" />
        Женщина
      </label>
    </div>

    <multi-selector-field
      title="Группа клиентов"
      :options="['VIP', 'Проблемные', 'ОМС']"
      :value.sync="client.group"
    />
    <error-input error="empty" v-if="!client.group.length" />

    <selector-field
      :options="['Иванов', 'Захаров', 'Чернышева']"
      title="Лечащий врач"
      :value.sync="client.doctor"
    />
    <checkbox-field title="Не отправлять СМС" :value.sync="client.message" />
  </div>
</template>

<script>
import SelectorField from "@/components/fields/SelectorField";
import CheckboxField from "@/components/fields/CheckboxField";
import MultiSelectorField from "@/components/fields/MultiSelectorField";
import DateField from "@/components/fields/DateField";
import PhoneField from "@/components/fields/PhoneField";
import { required, numeric } from "vuelidate/lib/validators";
import TextField from "@/components/fields/TextField";
import ErrorInput from "@/components/ErrorInput";

export default {
  name: "ClientInfo",
  props: {
    client: {
      type: Object,
      default: () => {}
    }
  },
  components: {
    ErrorInput,
    TextField,
    PhoneField,
    DateField,
    MultiSelectorField,
    CheckboxField,
    SelectorField
  },
  validations: {
    client: {
      surname: {
        required,
        alpha: val => /^[а-яё]*$/i.test(val)
      },
      name: {
        required,
        alpha: val => /^[а-яё]*$/i.test(val)
      },
      patronymic: {
        alpha: val => /^[а-яё]*$/i.test(val)
      },
      birthday: {
        required
      },
      phone: {
        required,
        numeric,
        phone: val => /^([7][0-9]{10})?$/.test(val)
      }
    }
  },
  updated() {
    this.client.valid = !this.$v.client.$invalid;
  }
};
</script>
<style scoped lang="scss">
.client-info__gender {
  display: flex;
  flex-direction: column;
  font-size: 1.5rem;
  text-align: left;
}
</style>
