<template>
  <table class="observation_main">
    <thead>
      <tr>
        <th class="colum1">{{ "reservation_detail.table.price" }}</th>
        <th class="colum2">{{ "reservation_detail.table.price" }}</th>
        <th class="colum3">{{ "reservation_detail.table.price" }}</th>
        <th class="colum4">{{ "reservation_detail.table.price" }}</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="(itemTable, index) in dataObservation"
        :key="index"
        class="dataTable"
      >
        <td>
          {{ itemTable.dataColum1 }}
        </td>
        <td>
          {{ itemTable.dataColum2 }}
        </td>
        <td>
          {{ itemTable.dataColum3 }}
        </td>
        <td class="data_price">
          <p>
            {{ itemTable.dataColum4 }}
          </p>
          <button @click="handelConfirmDele" class="Delete_history">
            {{ itemTable.dataColum5 }}
          </button>
          <p>
            {{ itemTable.dataColum6 }}
          </p>
          <button @click="handelCompose" class="compose_message">
            {{ itemTable.dataColum7 }}
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import "@/assets/views/Observation.css";
export default {
  name: "ObservationComponents",
  setup() {
    const dataObservation = [
      {
        dataColum1: "562",
        dataColum2: "【閉店】TIME SHARING 渋谷宮益坂2C",
        dataColum3: `ご希望日時
1. 2022年10月25日（火） 13:30
2. 2022年10月24日（月） 13:30
3. 2022年10月27日（木） 16:30

利用希望時間：moth
利用予定人数：20名

利用目的：会議室

利用目的詳細：t3g34gwg452w452

見学で確認したいところ：5g2g2g45g2g5`,
        dataColum4: `見学NG

キャンセル理由：
ご希望の日程では、ご利用できません。`,
        dataColum5: "履歴削除",
        dataColum6: "担当者にメッセージを送る",
        dataColum7: "メッセージを作成",
      },
    ];
    const handelConfirmDele = () => {
      confirm("履歴を削除します。よろしいですか？");
    };
    const handelCompose = () => {};
    return {
      dataObservation,
      handelConfirmDele,
      handelCompose,
    };
  },
};
</script>

<style>
</style>