<template lang="jade">
label.mdl-radio.mdl-js-radio(v-bind:for.once='id' v-bind:class='{ "is-disabled": disabled, "is-checked": isChecked }')
  input.mdl-radio__button(v-bind:id.once='id' type='radio' v-bind:name.once='name' v-bind:value='value' v-model='checked' v-bind:disabled='disabled')
  span.mdl-radio__label
    slot
</template>

<script>
import propFill from '../mixins/prop-fill'

export default {
  props: {
    id: String,
    name: String,
    value: {
      required: true
    },
    checked: {
      required: true,
      twoWay: true
    },
    disabled: {
      fill: true
    }
  },
  computed: {
    isChecked () {
      return this.checked === this.value
    }
  },
  ready () {
    componentHandler.upgradeElements(this.$el)
  },
  mixins: [propFill]
}
</script>
