<template>
  <div class="shopping-cart">
    <div class="cart-title">購物籃</div>
    <div class="item" v-for="item in items" :key="item.id">
      <img :src="item.image" alt="" />
      <div class="item-introduce">
        <div class="item-name">{{ item.name }}</div>
        <div class="item-quantity">
          <div class="item-minus" @click.stop.prevent="quantityMinus(item.id)">
            -
          </div>
          <div class="initial">{{ item.quantity }}</div>
          <div class="item-plus" @click.stop.prevent="quantityPlus(item.id)">
            +
          </div>
        </div>
        <div class="item-cost">{{ item.price }}</div>
      </div>
    </div>
    <div class="cart-cost1">
      <div>運費</div>
      <div>{{ this.transportFee | howMuch }}</div>
    </div>
    <div class="cart-cost2">
      <div>小計</div>
      <div class="total-cost">{{ totalPrice() }}</div>
    </div>
  </div>
</template>
<script>
const dummydata = {
  items: [
    {
      id: 0,
      quantity: 1,
      name: "破壞補丁修身牛仔褲",
      image: "https://i.imgur.com/TJDcjXQ.png",
      price: 3999,
    },
    {
      id: 1,
      quantity: 1,
      name: "直筒牛仔褲",
      image: "https://i.imgur.com/CddydHx.png",
      price: 1299,
    },
  ],
};
export default {
  props: {
    transportFee: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      items: [],
    };
  },
  created() {
    this.fetchItems();
  },
  methods: {
    fetchItems() {
      this.items = dummydata.items;
    },
    quantityPlus(id) {
      this.items[id].quantity++;
    },
    quantityMinus(id) {
      if (this.items[id].quantity > 0) {
        this.items[id].quantity--;
      }
    },
    totalPrice() {
      let total = 0;
      for (let i = 1; i <= this.items.length; i++) {
        total += this.items[i - 1].quantity * this.items[i - 1].price;
      }
      return total + this.transportFee;
    },
  },
  filters: {
    howMuch(target) {
      if (target === 0) {
        return "免費";
      }else{
        return target
      }
    },
  },
};
</script>