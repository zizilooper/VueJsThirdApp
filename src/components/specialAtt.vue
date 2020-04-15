<template>
  <div>
    <button class="btn" @click="changeYou">Special</button>

  </div>
</template>

<script>
export default {
  name: "SpecialAtt",
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

      if (mon.length !== 0) {
        const num1 = Math.floor(Math.random("1", "2") * 8);
        const num2 = Math.floor(Math.random("1", "2") * 8);

        if (num1 > num2) {
          mon = mon.splice(0, num1);
          you = you.splice(0, num2);
        } else {
          mon = mon.splice(0, num2);
          you = you.splice(0, num1);
        }

        this.num1.push(num1);
        this.num2.push(num2);

        this.$emit("AttYou", you);
       
      } else if (mon.length == 0) {
        alert("you winner");
      }
    },
  },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.btn {
  color: blueviolet;
  background: rgb(34, 18, 6);
  width: 90px;
  border-radius: 5px;
  margin: auto;

}
</style>
