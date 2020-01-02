<template>
  <div class="home">
    <h1>Calculator</h1>
    <div style="margin-bottom: 10px;">
      <input type="number" v-model="total" maxlength="4">
    </div>
    <div>
      <PerPanel v-for="p in panels" v-bind:total="total" v-bind:percent="p"
        v-bind:key="p"/>
    </div>
  </div>
</template>

<script>
import PerPanel from '@/components/PerPanel.vue';

export default {
  name: 'home',
  components: {
    PerPanel,
  },
  data() {
    return {
      total: 0,
      panels: [0.5, 0.4, 0.3, 0.2, 0.1],
    };
  },
};
</script>
