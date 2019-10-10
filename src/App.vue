<template>
  <div class="test">
    <select-option :list="list" :value="parent" @change="changeParent">
    </select-option>

    <div v-for="(child, index) in parent.value" :key="index">
      <select-option :list="child.value" @change="changeChild">
      </select-option>
    </div>
  </div>
</template>

<script>
import SelectOption from './SelectOption'

export default {
  name: 'Test',

  components: { SelectOption },

  data() {
    return {
      list: [
        {
          key: 'key1',
          value: [
            {
              key: 'key11',
              value: [
                {
                  key: 'key111',
                  value: 'value111'
                },
                {
                  key: 'key112',
                  value: 'value112'
                }
              ]
            },
            {
              key: 'key12',
              value: [
                {
                  key: 'key121',
                  value: 'value121'
                },
                {
                  key: 'key122',
                  value: 'value122'
                }
              ]
            },
            {
              key: 'key13',
              value: [
                {
                  key: 'key131',
                  value: 'value131'
                },
                {
                  key: 'key132',
                  value: 'value132'
                }
              ]
            }
          ]
        },
        {
          key: 'key2',
          value: [
            {
              key: 'key21',
              value: [
                {
                  key: 'key211',
                  value: 'value211'
                },
                {
                  key: 'key212',
                  value: 'value212'
                }
              ]
            },
            {
              key: 'key22',
              value: [
                {
                  key: 'key221',
                  value: 'value221'
                },
                {
                  key: 'key222',
                  value: 'value222'
                }
              ]
            },
            {
              key: 'key23',
              value: [
                {
                  key: 'key231',
                  value: 'value231'
                },
                {
                  key: 'key232',
                  value: 'value232'
                }
              ]
            }
          ]
        }
      ],
      parent: {},
    }
  },

  beforeMount() {
    this.parent = this.list[1]
  },

  methods: {
    changeParent(item) {
      this.parent = item
    },
    changeChild(item) {
      console.log(item)
    }
  }
}
</script>
