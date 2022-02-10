<template>
  <div>
    <header>
      <!--navbar--->
      <Navbar />
    </header>
    <div class="just-block"></div>
    <div class="main-container">
      <div class="left-container">
        <!--stepper here-->
        <Stepper :nowStep="nowStep" />
        <div class="form-container">
          <form id="a-form">
            <div class="form-box">
              <Form1 v-show="nowStep === 1" @userChange="updateUser" />
              <Form2 v-show="nowStep === 2" @feeChange="handleFee" />
              <Form3 v-show="nowStep === 3" @cardChange="updateCard" />
            </div>
          </form>
        </div>
      </div>
      <div class="right-container">
        <ShoppingCart :transportFee="transportFee" />
      </div>
      <div id="btn-control" class="control-panel">
        <button
          class="btn-before"
          v-if="nowStep !== 1"
          @click.stop.prevent="btnPrev"
        >
          ← 上一步
        </button>
        <button
          class="btn-next"
          v-if="nowStep !== 3"
          @click.stop.prevent="btnNext"
        >
          下一步 →
        </button>
        <button
          type="submit"
          class="btn-finish"
          v-if="nowStep === 3"
          @click.stop.prevent="handleData"
        >
          確認下單
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Form1 from "@/components/Form1.vue";
import Form2 from "@/components/Form2.vue";
import Form3 from "@/components/Form3.vue";
import ShoppingCart from "@/components/ShoppingCart.vue";
import Stepper from "@/components/Stepper.vue";

export default {
  name: "Home",
  components: {
    Navbar,
    Form1,
    Form2,
    Form3,
    ShoppingCart,
    Stepper,
  },
  data() {
    return {
      nowStep: 1,
      transportFee: 0,
      allProfiles: {
        gender: "",
        name: "",
        tel: "",
        email: "",
        city: "",
        address: "",
        cardName: "",
        cardNumber: "",
        exp: "",
        safeCode: "",
      },
    };
  },
  methods: {
    btnNext() {
      this.nowStep++;
    },
    btnPrev() {
      this.nowStep--;
    },
    handleFee(fee) {
      this.transportFee = fee;
    },
    updateUser(user) {
      this.allProfiles.name = user.name;
      this.allProfiles.tel = user.tel;
      this.allProfiles.email = user.email;
      this.allProfiles.city = user.city;
      this.allProfiles.gender = user.gender;
      this.allProfiles.address = user.address;
    },
    updateCard(card) {
      this.allProfiles.cardName = card.cardName;
      this.allProfiles.cardNumber = card.cardNumber;
      this.allProfiles.exp = card.exp;
      this.allProfiles.safeCode = card.safeCode;
    },
    handleData() {
      console.log(this.allProfiles);
    },
  },
};
</script>
