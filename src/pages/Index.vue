<template>
  <q-page class="flex flex-center">
      <div class="q-pa-md" style="max-width: 300px">

    <div class="q-gutter-md">

      <q-select
        outlined multiple
        square
        label="Тип кузова"
        v-model="model"
        :options="options"
        style="width: 180px"
        class="select"
        options-selected-class="text-selected"
        :menu-offset="[0, 20]"
        counter
        hint="Выбранно"
        :hide-selected="true"
      >
        <template
          class="mb"
          v-slot:option="{itemProps, itemEvents, opt}"
        >
          <q-item
            v-close-popup
            v-bind="itemProps"
            v-on="itemEvents"
            class="item"
          >
            <q-item-section>
                <q-checkbox
                  v-model="model"
                  :label="opt.value"
                  :val="opt"
                />
            </q-item-section>
          </q-item>
        </template>
      </q-select>
    </div>
      </div>
  </q-page>
</template>

<script>
const options = [
  {
    value: 'Задняя',
    id: 1
  },
  {
    value: 'Платформа',
    id: 2
  },
  {
    value: 'Рефрежиратор',
    id: 3
  },
  {
    value: 'Автовоз',
    id: 4
  }
]

export default {
  data () {
    return {
      model: [],
      options
    }
  }
}
</script>
<style lang="scss">
@import '../css/quasar.variables';

.select {
  margin-bottom: 30px;
  color: $lightGrey;
  & .q-select__dropdown-icon {
    font-size: 27px;
    font-weight: bold;
    color: $text;
  }
  & .q-field__control {
    color: $lightGrey;
  }
  &.q-field--float .q-field__label {
    transform: none;
  }
}
.item {
  font-size: 14px;
  color: $lightGrey;
  & .q-checkbox__inner {
      & .q-checkbox__bg {
        border-color: $text
      }
  }
  & .q-checkbox__inner--truthy {
    & .q-checkbox__bg {
        border-color: $primary;
      }
  }
}

.focused {
  border-color: $primary;
}

.text-selected {
  font-size: 14px;
  color: $text;
}
</style>
