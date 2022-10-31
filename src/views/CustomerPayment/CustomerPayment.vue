<template>
  <div class="customer_payment">
    <div>{{ itemHeader }}</div>
    <img src="@/assets/creditcardcustomer.png" alt="" />
    <div>{{ itemFooter }}</div>
  </div>
</template>

<script>
export default {
  name: "CustomerPayment",
  setup() {
    const itemHeader = `クレジットカードにエラーが発生したため、変更できませんでした。
＜可能性のあるエラー＞
・VISA、MasterCard、DinersClub以外のカード情報を入力した。`;
 const itemFooter = `・カード番号に誤りがある。
・セキュリティーコードに誤りがある。
・エラーコード = 101
最初からやり直してください。`;
return {itemHeader,itemFooter }
  },
};
</script>

<style>
</style>