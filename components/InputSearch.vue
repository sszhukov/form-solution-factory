<template>
  <div class="search">
    <input type="text" class="input-search" placeholder="Поиск по системе">
    <div class="icon">
      🔍
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .search {
    display: flex;
    justify-content: space-between;
    padding: 3px 10px;
    margin: 20px;
    border: 1px solid rgba(0, 0, 0, .1);

    .input-search {
      border: none;
      outline: none;
      flex-grow: 1;

      &:active, &:hover, &:focus {
        outline: 0;
        outline-offset: 0;
      }
    }
  }
</style>
