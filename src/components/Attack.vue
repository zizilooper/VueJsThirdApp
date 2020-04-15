<template>
  <div>
    <button class="btn" @click="changeYou">Attack</button>
  </div>
</template>

<script>
export default {
  name: "Attack",
  props: {
    monArr: Array,
    youArr: Array,
  },
  data: () => ({
    num1: [],
    num2: [],
  }),
  methods: {
    changeYou() {
      let you = this.youArr;
      let mon = this.monArr;

      if (you.length !== 0) {
        const num1 = Math.floor(Math.random("1", "2") * 8);
        const num2 = Math.floor(Math.random("1", "2") * 8);

        if (num1 > num2 && this.youArr.length !== 0) {
          you = you.splice(0, num1);
          mon = mon.splice(0, num2);
        } else {
          you = you.splice(0, num2);
          mon = mon.splice(0, num1);
        }

        this.num1.push(num1);
        this.num2.push(num2);

        this.$emit("AttYou", you);
        this.$emit("Attmon", mon);
      } else if (you.length == 0) {
        alert("game over");
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
