<template>
  <div class="form" >
    <h1>運送方式</h1>
    <div class="part2">
      <div class="transport">
        <label for="standard">
          <div class="standard">
            <input
              name="transport"
              type="radio"
              id="standard"
              class="standard-circle"
              @click="standard"
            />
            <div class="transport-introduce trans-how">標準運送</div>
            <div class="transport-introduce trans-cost">免費</div>
            <div class="transport-introduce trans-time">約 3~7 個工作天</div>
          </div>
        </label>
        <label for="DHL">
          <div class="DHL">
            <input
              name="transport"
              type="radio"
              id="DHL"
              class="DHL-circle"
              @click="dhl"
            />
            <div class="transport-introduce trans-how">DHL運送</div>
            <div class="transport-introduce trans-cost">$500</div>
            <div class="transport-introduce trans-time">48小時內送達</div>
          </div>
        </label>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      transportFee: 0,
    };
  },
  methods: {
    standard() {
      this.transportFee = 0;
      this.$emit('feeChange', this.transportFee)
    },
    dhl() {
      this.transportFee = 500;
      this.$emit('feeChange', this.transportFee)
    },
  },
};
</script>