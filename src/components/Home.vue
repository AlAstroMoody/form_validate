<template>
  <div class="client">
    <h1>Форма создания клиента</h1>
    <section class="client__form">
      <client-info class="client__info" :client.sync="client" />
      <client-passport class="client__info" :passport.sync="passport" />
      <client-address class="client__info" :address.sync="address" />
    </section>
    <button
      @click="sendInfo"
      :disabled="!(client.valid && address.valid && passport.valid)" >
      Создать клиента
    </button>
  </div>
</template>

<script>
import ClientInfo from "@/components/ClientInfo";
import ClientPassport from "@/components/ClientPassport";
import ClientAddress from "@/components/ClientAddress";

export default {
  name: "Home",
  data() {
    return {
      client: {
        surname: "",
        name: "",
        birthday: "",
        phone: "",
        gender: "male",
        doctor: "",
        patronymic: "",
        message: true,
        group: [],
        valid: false
      },
      address: {
        index: "",
        country: "",
        region: "",
        city: "",
        street: "",
        house: "",
        valid: false
      },
      passport: {
        documentType: "",
        series: "",
        ID: "",
        organization: "",
        dateOfIssue: "",
        valid: false
      }
    };
  },
  components: { ClientAddress, ClientPassport, ClientInfo },
  methods: {
    sendInfo() {
      alert("Запись о клиенте внесена!");
      console.log(this.client, this.address, this.passport);
    }
  }
};
</script>

<style scoped lang="scss">
.client__form {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  .client__info {
    color: gainsboro;
    width: 30%;
    min-width: 350px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    padding: 5px;
    border-radius: 5px;
    margin: 1%;
  }
  .client__info:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }
}
</style>
