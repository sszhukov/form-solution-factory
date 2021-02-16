<template>
  <div class="condition-row">
    <div class="condition-name position">
      <LogicalOperator v-if="number > 1 && !main" class="logical-operator" mode="or" />
      {{ name }} {{ number || '' }}
    </div>
    <div class="condition-select position" :class="{main: main}">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    },
    number: {
      type: Number,
      default: 0
    },
    main: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
  .condition-row {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 15px 0;
    font-size: 12px;

    .logical-operator {
      margin-right: 10px;
    }

    .condition-name {
      display: flex;
      align-items: center;
      width: 25%;
      min-width: 100px;
      text-align: left;
    }

    .condition-select {
      flex-grow: 1;
      margin-right: 30px;
    }

    .main {
      margin: 10px 0;
    }
  }
</style>
