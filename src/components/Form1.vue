<template>
  <div class="form" @change="handleUser">
    <h1>寄送地址</h1>
    <div class="part1">
      <div class="form-row title">
        <label>稱謂</label>
        <select name="title" id="title" v-model="userProfile.gender">
          <option value="" disabled selected>稱謂</option>
          <option value="male">先生</option>
          <option value="female">小姐</option>
        </select>
      </div>
      <div class="form-row name">
        <label for="">姓名</label>
        <input
          type="text"
          placeholder="請輸入姓名"
          v-model="userProfile.name"
        />
      </div>
      <div class="form-row telephone">
        <label for="">電話</label>
        <input type="text" placeholder="請輸入電話" v-model="userProfile.tel" />
      </div>
      <div class="form-row email">
        <label for="">E-mail</label>
        <input
          type="text"
          placeholder="請輸入電子郵件"
          v-model="userProfile.email"
        />
      </div>
      <div class="form-row city">
        <label for="">縣市</label>
        <select name="city" id="city" v-model="userProfile.city">
          <option value="" disabled selected>請選擇縣市</option>
          <option value="taipei">臺北市</option>
          <option value="New Taipei">新北市</option>
          <option value="Keelung">基隆市</option>
          <option value="Taoyuan">桃園市</option>
          <option value="Miaoli">苗栗縣</option>
          <option value="Taichung">臺中市</option>
          <option value="Tainan">臺南市</option>
          <option value="Kaohsiung">高雄市</option>
          <option value="Hsinchu">新竹市</option>
          <option value="Chiayi">嘉義市</option>
          <option value="Changhua">彰化縣</option>
          <option value="Nantou">南投縣</option>
          <option value="Yunlin">雲林縣</option>
          <option value="Pingtung">屏東縣</option>
          <option value="Yilan ">宜蘭縣</option>
          <option value="Taitung">台東縣</option>
          <option value="Penghu">澎湖縣</option>
        </select>
      </div>
      <div class="form-row adress">
        <label for="">地址</label>
        <input
          type="text"
          placeholder="請輸入地址"
          v-model="userProfile.address"
        />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      userProfile: {
        gender: "",
        name: "",
        tel: "",
        email: "",
        city: "",
        address: "",
      },
    };
  },
  methods: {
    handleUser() {
      this.$emit("userChange", this.userProfile);
    },
  },
};
</script>
