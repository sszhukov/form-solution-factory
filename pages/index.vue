<template>
  <div class="container">
    <div class="title">
      Добавить опрос
    </div>
    <Condition
      v-for="(condition, index) in conditions"
      :key="index"
      v-model="conditions[index]"
      :conditions="staticConditions"
      :num-index="index"
      @input="getCondition"
      @remove="remove(index)"
    />
    <ConditionAdding @click.native="addCondition" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      conditions: [],
      staticConditions: [
        {
          id: 1,
          name: 'Возраст респондента',
          type: 'range',
          optionName: 'Диапазон',
          option: []
        },
        {
          id: 2,
          name: 'Тип карты лояльности',
          type: 'single',
          optionName: 'Тип',
          options: [
            { id: 1, name: 'Gold' },
            { id: 2, name: 'Platinum' }
          ]
        }
      ]
    }
  },
  methods: {
    addCondition () {
      this.conditions.push({})
    },
    remove (index) {
      this.conditions = this.conditions.filter((el, indx) => indx !== index)
    }
  }
}
</script>

<style lang="scss" scoped>

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin: 0 auto;
  margin-left: 100px;
  min-height: 100vh;

  .title {
    width: 100%;
    padding: 10px 20px;
    color: rgba(0, 0, 0, .2);
    font-weight: bold;
    text-align: left;
  }
}

</style>
