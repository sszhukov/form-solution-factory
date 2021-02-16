<template>
  <button class="button">
    <div v-if="add" class="button__icon">
      ➕
    </div>
    <div v-else-if="remove" class="button__icon">
      🗑
    </div>
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    remove: Boolean,
    add: Boolean
  }
}
</script>

<style lang="scss" scoped>
  .button {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 30px;
    border: 2px solid black;
    border-radius: 5px;
    cursor: pointer;

    .button__icon {
      margin: auto 10px auto 0;
    }
  }
</style>
