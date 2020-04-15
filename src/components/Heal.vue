<template>
  <div>
    <button class="btn" @click="changeYou">Heal</button>
  </div>
</template>

<script>
export default {
  name: "Heal",
  props: {
    monArr: Array,
    youArr: Array,
  },
  data: () => ({
   
  }),
  methods: {
    changeYou() {
      let you = this.youArr;
      let mon = this.monArr;

      if (mon.length < you.length && you.length <= 9) {
        const num2 = Math.floor(Math.random("1", "2") * 8);
        this.youArr = this.youArr.push(num2);
        this.$emit("AttYou", you);
        this.num2.push(num2);
      }
    },
  },
};
</script>

<style scoped lang="scss">
.btn {
  color: blueviolet;
  background: rgb(34, 18, 6);
  width: 90px;
  border-radius: 5px;
  margin: auto;
}
</style>
