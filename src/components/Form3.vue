<template>
  <div class="form" @change="handleCard">
    <h1>付款資訊</h1>
    <div class="part3">
      <div class="form-row card-name">
        <label for="">持卡人姓名</label>
        <input type="text" placeholder="請輸入持卡人姓名" v-model="payment.cardName" />
      </div>
      <div class="form-row card-number">
        <label for="">卡號</label>
        <input type="text" placeholder="1111 2222 3333 4444" v-model="payment.cardNumber" />
      </div>
      <div class="form-row card-date">
        <label for="">有效期限</label>
        <input type="text" placeholder="MM/YY" v-model="payment.exp" />
      </div>
      <div class="form-row safe-number">
        <label for="">安全碼</label>
        <input type="text" placeholder="123" v-model="payment.safeCode" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      payment: {
        cardName: "",
        cardNumber: "",
        exp: "",
        safeCode: "",
      },
    };
  },
    methods: {
    handleCard() {
      this.$emit("cardChange", this.payment);
    },
  },
};
</script>