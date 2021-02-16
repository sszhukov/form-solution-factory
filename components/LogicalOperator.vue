<template>
  <div class="logical-operator">
    <span v-if="mode === 'and'" class="operator-title">И</span>
    <span v-else-if="mode === 'or'" class="operator-title">или</span>
  </div>
</template>

<script>
export default {
  props: {
    mode: {
      type: String,
      default: 'and'
    }
  }
}
</script>

<style lang="scss" scoped>
  .logical-operator {
    display: flex;
    width: 35px;
    height: 30px;
    border-radius: 5px;
    background: rosybrown;

    .operator-title {
      font-size: 10px;
      margin: auto;
    }
  }
</style>
