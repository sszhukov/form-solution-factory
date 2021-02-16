<template>
  <div class="side-panel">
    <div class="red-circle menu-circle" />
    <div class="menu">
      <nuxt-link
        v-for="(link, index) in links"
        :key="index"
        class="item"
        exact
        active-class="active"
        :to="link.link"
      >
        <div class="menu-item__icon">
          {{ link.icons }}
        </div>
        <p class="menu-item__title">
          {{ link.name }}
        </p>
      </nuxt-link>
    </div>
    <div class="help menu-circle">
      ?
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      links: [
        { name: 'Опросы', link: '/', icons: '📝' },
        { name: 'Пользователи', link: '/users', icons: '👥' },
        { name: 'Черные списки', link: '/black-lists', icons: '🚷' },
        { name: 'Кол-центр', link: 'call-center', icons: '☎️' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .side-panel {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 100vh;
    width: 100px;
    padding: 30px 0;
    font-size: 10px;
    border-right: 1px solid rgba(0, 0, 0, .1);
    border-bottom: 1px solid rgba(0, 0, 0, .1);

    .red-circle {
      background: red;
    }

    .menu {
      flex-grow: 1;
      width: 100%;
      margin: 15px 0;

      .item {
        display: flex;
        flex-direction: column;
        height: 80px;
        margin: 5px 5px 5px 5px;
        text-decoration: none;
        list-style: none;
        border: 2px solid transparent;
        border-radius: 5px;
        text-decoration: none;
        color: #000;

        &:hover {
          border: 2px solid rgb(181, 207, 157);
          color: rgb(181, 207, 157);
          background: none;
        }

        .menu-item__icon {
          margin: auto;
        }

        .menu-item__title {
          margin: auto;
        }
      }

      .active {
        background: rgb(201, 201, 201) !important;
        border: none !important;
        font-weight: bold;
        color: black !important;
      }
    }

    .help {
      border: 1px solid black;
    }

    .menu-circle {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 25px;
      height: 25px;
      border-radius: 50%;
    }
  }
</style>
