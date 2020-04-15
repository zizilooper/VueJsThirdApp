<template>
  <div>
    <h1>your cource:{{ youArr.length }}</h1>
    <h1>mons cource:{{ monArr.length }}</h1>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: {
    monArr: Array,
    youArr: Array,
  },
};
</script>
