<template>
  <div class="credit_card_main">
    <div class="credit_card_container">
      <div class="credit_card_header">{{ "credit_card.header" }}</div>
      <div class="credit_card_header_sub">
        {{ "credit_card.credit_card_accept" }}
      </div>
      <img src="@/assets/creditcard.png" alt="" class="credit_card_img" />
      <div class="credit_description">
        <li>{{ "credit_card.credit_description1" }}</li>
        <li>{{ "credit_card.credit_description2" }}</li>
        <li>{{ "credit_card.credit_description3" }}</li>
      </div>
      <div v-if="isError" class="errors_message">
        {{ "credit_card.error1" }}
      </div>
      <table class="credit_content_table">
        <thead>
          <tr>
            <th class="colum1"></th>
            <th class="colum2"></th>
          </tr>
        </thead>
        <tbody>
          <tr class="dataTable">
            <td class="dataTitle">
              {{ "credit_card.card_number" }}
            </td>
            <td class="dataContent">
              <input
                type="text"
                v-model="formData.cardNumber"
                placeholder="例：1234123412341234"
                class="input_card_number"
              />
              <div>{{ "credit_card.card_number_sub" }}</div>
            </td>
          </tr>
          <tr class="dataTable">
            <td class="dataTitle">
              {{ "credit_card.end_date" }}
            </td>
            <td class="dataContent">
              <div class="dataContent_date">
                <input
                  type="text"
                  v-model="formData.month"
                  class="input_card_number"
                />
                <span>/</span>
                <input
                  type="text"
                  v-model="formData.year"
                  class="input_card_number"
                />
              </div>
              <div>{{ "credit_card.end_date_sub" }}</div>
            </td>
          </tr>
          <tr class="dataTable">
            <td class="dataTitle">
              {{ "credit_card.card_own" }}
            </td>
            <td class="dataContent">
              <input
                type="text"
                v-model="formData.cardOwner"
                placeholder="（例：TARO YAMADA"
                class="input_card_number"
              />
              <div>{{ "credit_card.card_own_sub" }}</div>
            </td>
          </tr>
          <tr class="dataTable">
            <td class="dataTitle">
              {{ "credit_card.security" }}
            </td>
            <td>
              <div class="dataContent_security">
                <input
                  type="text"
                  v-model="formData.securityText"
                  class="input_security"
                />
                <img src="@/assets/img_securitycode.gif" alt="" />
                <div class="sub_security">
                  <div>{{ "credit_card.security_sub" }}</div>
                  <div>{{ "credit_card.security_sub1" }}</div>
                </div>
              </div>
              <div v-if="isError" class="errors_message">
                {{ "credit_card.error2" }}
              </div>
            </td>
          </tr>
          <tr class="dataTableBtn">
            <td class="dataTitleBtn"></td>
            <td>
              <button @click="handleSubmit" class="dataContent_btn">
                {{ "credit_card.btn" }}
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import "@/assets/views/CreditCard.css";
export default {
  name: "CreditCard",
  setup() {
    const isError = ref(false);
    const formData = {
      cardNumber: "",
      month: "",
      year: "",
      cardOwner: "",
      securityText: "",
    };
    const handleSubmit = () => {
      if (!formData.securityText) {
        isError.value = true;
        return;
      } else {
        isError.value = false;
        // router.push
      }
    };
    return { isError, formData, handleSubmit };
  },
};
</script>

<style>
</style>