<template>
  <div class="main_reservation">
    <div v-for="(item, index) in dataDetail" :key="index">
      <FormLayout v-if="item.type === 'text'" :labelText="item.label">
        {{ item.text }}
      </FormLayout>
      <FormLayout v-if="item.type === 'table'" :labelText="item.label">
        <table class="detail_reservation_table">
          <thead>
            <tr>
              <th class="colum1"></th>
              <th class="colum2">
                {{ "reservation_detail.table.people" }}
              </th>
              <th class="colum3">{{ "reservation_detail.table.price" }}</th>
              <th class="colum4">{{ "reservation_detail.table.price_per" }}</th>
              <th class="colum5">{{ "reservation_detail.table.total" }}</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(itemTable, index) in item.text"
              :key="index"
              class="dataTable"
            >
              <td>
                <span class="">
                  {{ itemTable.dataColum1 }}
                </span>
              </td>
              <td>
                <span class="">
                  {{ itemTable.dataColum2 }}
                </span>
              </td>
              <td>
                <span class="">
                  {{ itemTable.dataColum3 }}
                </span>
              </td>
              <td>
                <span class="">
                  {{ itemTable.dataColum4 }}
                </span>
              </td>
              <td>
                <span class="">
                  {{ itemTable.dataColum5 }}
                </span>
              </td>
            </tr>
          </tbody>
        </table>
      </FormLayout>
      <FormLayout v-if="item.type === 'textChild'" :labelText="item.label">
        <div v-for="(itemChild, index) in item.text" :key="index">
          <div class="text_child">
            <div class="text_child_content">
              {{ itemChild.content1 }}
            </div>
            <div class="text_child_content">
              {{ itemChild.content2 }}
            </div>
          </div>
        </div>
      </FormLayout>
    </div>
    <div class="message">{{ informationNote }}</div>
    運営事務局へのメッセージ
    <FormLayout :labelText="'内容'" :isRequired=true>
      <textarea disabled  rows="5" class="textarea"></textarea>
    </FormLayout >
    <button class="btn_submit">メッセージ送信</button>
  </div>
</template>

<script>
import "@/assets/views/ReservationDetail.css";
import FormLayout from "@/components/FormLayout/FormLayout.vue";
export default {
  components: { FormLayout },
  name: "ReservationDetail",
  setup() {
    const informationNote = "現在、メッセージは送信できません。";
    const dataCompletionDate = "2022年10月20日（木）14:44";
    const dataStatus = " オーナーによる否認（テスト予約の為）";
    const dataMethodPay = "銀行振込";
    const dataDetail = [
      {
        type: "text",
        label: /*t*/ "reservation_detail.completion_date",
        text: "2022年10月20日（木）14:44",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.status",
        text: "X オーナーによる否認（テスト予約の為）",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.method_pay",
        text: "銀行振込",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.space_name",
        text: "Mace 千駄ヶ谷",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.plan_name",
        text: "会議・セミナー限定料金",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.user_date",
        text: "2022年11月26日（土）",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.use_time",
        text: "09:30 - 12:30",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.people",
        text: "8 名",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.user_purpose",
        text: "パーティー",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.user_purpose_detail",
        text: "11111122222",
      },
      {
        type: "table",
        label: /*t*/ "reservation_detail.register_detail",
        text: [
          {
            dataColum1: "(09:30-10:00) 会議・セミナー限定料金",
            dataColum2: "8 名",
            dataColum3: "6,750 円",
            dataColum4: "0 円／人",
            dataColum5:
              "6,750 円  ルーム料金:  6,750 円  一人あたり料金: 0 円／人",
          },
        ],
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.total_use_area",
        text: "計40,500.00円（税抜） 44,550円（税込",
      },
      {
        type: "textChild",
        label: /*t*/ "reservation_detail.buy",
        text: [
          {
            content1: "キッチン（1時間/個）: 8,000円 x 2 個",
            content2:
              "キッチン＆カウンターがご利用いただけます。最低利用時間は3時間になります。",
          },
          {
            content1: "キッチン（1時間/個）: 8,000円 x 2 個",
            content2:
              "キッチン＆カウンターがご利用いただけます。最低利用時間は3時間になります。",
          },
        ],
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.total_price",
        text: "31,409円（税抜） 34,550円（税込）",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.total",
        text: "71,909円（税抜） 79,100円（税込）",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.confirm_space",
        text: `■飲食について
持ち込みをされる場合は以下の回答欄で事前に申告をお願いいたします。
内容によっては、【会議・セミナー料金】ではお受けできない場合がございます。

■パーティー利用について
パーティー利用にもお勧めのスペースとなりますが、クラブのような爆音は禁止となります。
楽器演奏などある場合は事前にご相談ください。`,
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.answer",
        text: "yyyyyyyyyyyyy",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.message",
        text: `■ゴミ回収について
・事前申込なしで、当日に依頼された場合、現金精算のみのご案内となります。クレジットカード決済、後払いは出来ません。
・会場に釣銭のご用意はございませんのでご注意ください。`,
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.information",
        text: "yyyyyyyyyyyyy",
      },
      {
        type: "text",
        label: /*t*/ "reservation_detail.receipt",
        text: "領収書は決済が完了した場合のみ発行させていただいております。",
      },
    ];

    return {
      dataDetail,
      dataCompletionDate,
      dataStatus,
      dataMethodPay,
      informationNote,
    };
  },
};
</script>

<style>
</style>