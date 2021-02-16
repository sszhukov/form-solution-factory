<template>
  <select v-model="select" class="input select-condition">
    <option disabled>
      Выберите
    </option>
    <option v-for="option in options" :key="option.id" :value="option">
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      default () {
        return []
      }
    }
  },
  computed: {
    select: {
      get () {
        return this.value
      },
      set (value) {
        this.$emit('input', value)
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

  .select-condition {
    width: 100%;
  }
</style>
