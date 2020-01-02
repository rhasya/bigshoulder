<template>
  <div>
    <div>
      <span style="font-size: 20px;">{{ label }}</span>
      <span> - </span>
      <span style="font-size: 20px;">{{ amount }}</span>
    </div>
    <div class="border" >
      <span class="info" v-for="(c, i) in coins" :key="coinInfo[i] + '' + percent">
        {{ `${c} x ${coinInfo[i]}` }} Coin
      </span>
    </div>
  </div>
</template>
<script>
export default {
  name: 'PerPanel',
  props: ['total', 'percent'],
  computed: {
    coinInfo() {
      return [50, 10, 5, 1];
    },
    label() {
      return `${this.percent * 100}%`;
    },
    amount() {
      return Math.floor(this.total * this.percent);
    },
    coins() {
      let v = this.amount;
      const r = [];
      for (let i = 0; i < this.coinInfo.length; i += 1) {
        r.push(Math.floor(v / this.coinInfo[i]));
        v %= this.coinInfo[i];
      }
      return r;
    },
  },
};
</script>
<style>
div.border {
  border: 1px solid gray;
  margin-top: 5px;
  margin-bottom: 10px;
}
.info + .info:before {
  content: '|';
}
</style>
