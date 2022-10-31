<template>
  <div class="main_ObservationDetail">
    <div
      v-for="(item, index) in dataDetail"
      :key="index"
      class="main_observationDetail_item"
    >
      <FormLayout v-if="item.type === 'text'" :labelText="item.label">
        <div class="data_text">
          {{ item.text }}
        </div>
      </FormLayout>
      <FormLayout v-if="item.type === 'textButton'" :labelText="item.label">
        <div class="data_text">
          {{ item.text }}
        </div>
        <buttons @click="handelFocus" class="data_text_btn">
          {{ item.textBtn }}
        </buttons>
      </FormLayout>
    </div>
    <div class="observation_message">
      <div class="message">{{ informationHistory }}</div>
    </div>
    <div id="observation_message_main">
      <div class="observation_message_client">
        <div class="sub_chat_client">{{ timeChatClient }}</div>
        <div class="chat_client">{{ timeChat }}</div>
      </div>
      <div class="observation_message_admin">
        <div class="sub_chat_admin">{{ timeChatClient }}</div>
        <div class="chat_admin">{{ timeChat1 }}</div>
      </div>
    </div>
    <FormLayout :labelText="'内容'" :isRequired="true">
      <textarea disabled rows="5" class="textarea"></textarea>
    </FormLayout>
    <button @click="handleSubmit" class="btn_submit">メッセージ送信</button>
  </div>
</template>

<script>
import "@/assets/views/ObservationDetail.css";
import FormLayout from "@/components/FormLayout/FormLayout.vue";
export default {
  name: "ObservationDetail",
  components: { FormLayout },
  setup() {
    const informationHistory = "メッセージ履歴";
    const timeChat = "test";
    const timeChat1 = "test";
    const timeChatClient =
      "（オーナー）TIME SHARING カスタマーセンター - 2022年10月19日（水）14:44";

    const dataDetail = [
      {
        type: "textButton",
        label: /*t*/ "reservation_detail.status",
        text: `見学NG
キャンセル理由：
ご希望の日程では、ご利用できません。`,
        textBtn: "メッセージを作成",
      },
      {
        type: "text",
        label: /*t*/ "observation_detail.id",
        text: " 562",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.space_name",
        text: " 【閉店】TIME SHARING 渋谷宮益坂2C",
      },
      {
        type: "text",
        label: /*t*/ "observation_detail.date_expect",
        text: `1. 2022年10月25日（火） 13:30
2. 2022年10月24日（月） 13:30
3. 2022年10月27日（木） 16:30`,
      },
      {
        type: "text",
        label: /*t*/ "observation_detail.date_expect_use",
        text: " moth",
      },
      {
        type: "text",
        label: /*t*/ "observation_detail.people",
        text: "20",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.user_purpose",
        text: "会議室",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.user_purpose_detail",
        text: "TEST",
      },
      {
        type: "text",
        label: /*t*/ "observation_detail.plate_check",
        text: "TEST",
      },
      
    ];
    const handleSubmit = () => {
      confirm("データの保存に失敗しました！");
    };
    const handelFocus = () => {
      console.log("test");
       document.getElementById("observation_message_main").focus();
      // count.value = count.value+1
    };

    return {
      dataDetail,
      informationHistory,
      timeChatClient,
      timeChat,
      timeChat1,
      handleSubmit,
      handelFocus,
    };
  },
};
</script>

<style>
</style>