<template>
  <div>
    <div>
      <span>{{ label }}</span>
      <span> - </span>
      <span>{{ amount }}</span>
    </div>
    <div class="border">
      <span class="info" v-for="(c, i) in coins" :key="coinInfo[i] + '' + percent">
        {{ `${c} x ${coinInfo[i]}` }}
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
      return this.total * this.percent;
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
}
.info + .info:before {
  content: '|';
}
</style>
