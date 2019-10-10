<template>
  <a-select :value="JSON.stringify(current.value)">
    <a-select-option v-for="item in list" :value="JSON.stringify(item.value)" @click="changeCurrent(item)">
      {{ item.key }}
    </a-select-option>
  </a-select>
</template>

<script>
export default {
  name: 'SelectOption',

  props: {
    list: {
      type: Array,
      default: () => []
    },
    value: {
      type: Object,
      default: () => {}
    }
  },

  data() {
    return {
      current: {}
    }
  },

  watch: {
    list() {
      this.resetCurrent()
    }
  },

  beforeMount() {
    this.resetCurrent()
  },

  methods: {
    resetCurrent() {
      this.current = this.value ? this.value : this.list[0]
    },
    changeCurrent(item) {
      this.current = item
      this.$emit('change', this.current)
    }
  }
}
</script>