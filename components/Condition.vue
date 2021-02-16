<template>
  <div class="condition" :class="{borderTop: numIndex > 0}">
    <LogicalOperator v-if="numIndex > 0" class="logical-operator" />
    <ConditionRow class="condition-row" name="Условие" :main="true" :number="numIndex + 1">
      <Select v-model="condition" :options="conditions" />
    </ConditionRow>

    <ConditionRow v-for="(rValue, index) in returnValue" :key="index" class="condition-row" :name="condition.optionName" :number="index + 1">
      <RangeCondition v-if="condition.type === 'range'" v-model="returnValue[index]" @input="submit" />
      <Select v-else-if="condition.type === 'single'" v-model="returnValue[index]" :options="condition.options" @input="submit" />
    </ConditionRow>

    <ConditionRow class="condition-row" :main="true">
      <div class="buttons">
        <Button class="remove" :remove="true" @click.native="remove">
          Удалить условие
        </Button>
        <Button v-if="condition.optionName" :add="true" @click.native="addRow">
          Добавить {{ condition.optionName.toLowerCase() }}
        </Button>
      </div>
    </ConditionRow>
  </div>
</template>

<script>
export default {
  props: {
    numIndex: {
      type: Number,
      default: 0
    },
    conditions: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      returnValue: [],
      condition: {}
    }
  },
  watch: {
    condition () {
      this.returnValue = [{}]
    }
  },
  methods: {
    addRow () {
      this.returnValue.push({})
    },
    submit () {
      this.$emit('input', { id: this.condition.id, values: this.returnValue })
    },
    remove () {
      this.$emit('remove', this.condition.id)
    }
  }
}
</script>

<style lang="scss" scoped>
  .condition {
    position: relative;
    width: 100%;
    padding: 0 20px;
    background: rgb(255, 224, 224);

    .logical-operator {
      position: absolute;
      top: -15px;
      left: 20px;
    }

    .condition-row {
      width: 100%;
    }

    .buttons {
      display: flex;
      flex-direction: row-reverse;
      justify-content: space-between;
      width: 100%;

      .remove {
        justify-self: end;
      }
    }
  }

  .borderTop {
    border-top: 1px solid rgba(0, 0, 0, .1);
  }
</style>
