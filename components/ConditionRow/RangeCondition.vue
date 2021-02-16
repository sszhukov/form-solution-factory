<template>
  <div class="range-condition">
    <div class="text">
      От
    </div>
    <input v-model.number="minValue" class="input min-value" type="text">
    <div class="text">
      До
    </div>
    <input v-model.number="maxValue" class="input max-value" type="text">
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  data () {
    return {
      minValue: 0,
      maxValue: 0
    }
  },
  computed: {
    range () {
      return {
        min: this.minValue,
        max: this.maxValue
      }
    }
  },
  watch: {
    range () {
      if (this.range.min >= 0 && this.range.max > 0 && this.range.max >= this.range.min) {
        this.$emit('input', this.range)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .input {
    height: 2.5em;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, .2);
    padding: 5px 10px;
  }

  .range-condition {
    display: flex;
    width: 100%;

    .text, .min-value, .max-value {
      margin: auto 0;
    }

    .min-value, .max-value {
      width: 100px;
      margin-left: 10px;
    }

    .min-value {
      margin-right: 10px;
    }
  }
</style>
