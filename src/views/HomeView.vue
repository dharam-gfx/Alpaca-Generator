<template>
  <div>
    <Alpacas></Alpacas>
  </div>
</template>

<script>

import Alpacas from './Alpaca.vue';
export default {
  data() {
    return {
      btnName: "btnName",
    }
  },
  components: {
    Alpacas
  }
}
</script>

<style  scoped></style>