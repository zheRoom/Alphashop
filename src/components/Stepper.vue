<template>
      <div class="stepper-panel" id="step-control">
      <h1 class="stepper-title">結帳</h1>
      <div class="stepper-container">
        <div class="step" :class="{active:nowStep===1,checked:nowStep>1}">
          <div class="circle-container"></div>
          <div class="label-container">寄送地址</div>
        </div>
        <div class="step" :class="{active:nowStep===2,checked:nowStep>2}">
          <div class="circle-container"></div>
          <span class="line"></span>
          <div class="label-container">運送方式</div>
        </div>
        <div class="step" :class="{active:nowStep===3}">
          <div class="circle-container"></div>
          <span class="line"></span>
          <div class="label-container">付款資訊</div>
        </div>
      </div>
    </div>
</template>
<script>
export default {
  props: {
    nowStep: {
      type: Number,
      required: true,
    },
  },
}
</script>