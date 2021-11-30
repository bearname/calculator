<template>
  <div :class="`${'tag' + (disabled ? '': ' tag--active')+ (clicked ? ' tag__clicked': '')}`"
      >
    <input class="tag__checkbox" type="checkbox" :checked="isChecked" :value="value" @change="updateInput"/>
    <span class="tag__title">{{ price }}₽</span>
    <span class="tag__descr">{{ duration }} </span>
  </div>
</template>

<script>
export default {
  name: "Tag",
  model: {
    prop: 'modelValue',
    event: 'change'
  },

  props: {
    value: { type: String },
    modelValue: { default: "" },
    trueValue: { default: true },
    falseValue: { default: false },
    disabled: {
      type: Boolean,
      default: false,
    },
    price: {
      type: String,
      default: '32 000',
    },
    duration: {
      type: String,
      default: '5 лет 5 мес.',
    },
  },
  emits: ['toggled'],

  data () {
    return {
      clicked: false,
    }
  },
  computed: {
    isChecked () {
      if (this.modelValue instanceof Array) {
        return this.modelValue.includes(this.value)
      }
      // Note that `true-value` and `false-value` are camelCase in the JS
      return this.modelValue === this.trueValue
    }
  },
  methods: {
    updateInput (event) {
      let isChecked = event.target.checked
      if (this.modelValue instanceof Array) {
        this.clicked = !this.clicked;
        let newValue = [...this.modelValue]
        if (isChecked) {
          newValue.push(this.value)
        } else {
          newValue.splice(newValue.indexOf(this.value), 1)
        }
        this.$emit('change', newValue)
      } else {
        this.$emit('change', isChecked ? this.trueValue : this.falseValue)
      }
    },

    // toggle (e) {
    //   console.log(e.target);
    //   this.clicked = !this.clicked;
    //   this.$emit('toggled')
    // }
  }
}
</script>

<style scoped>
.tag {
  position: relative;
  padding: 6px 12px;
  width: 158px;
  border-radius: 50px;
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 24px;
  text-align: center;
  background: #EEF0F2;
}

.tag--active {
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  color: #FFFFFF;
}

.tag__checkbox {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0;
}

.tag .tag__title {
  color: #000000;
}

.tag .tag__descr {
  padding-left: 5px;
  color: #545353;
}

.tag--active .tag__title,
.tag--active .tag__descr {
  color: #FFFFFF;
}

.tag__clicked {
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
}

.tag__clicked .tag__title,
.tag__clicked .tag__descr {
  color: #FFFFFF;
}

.tag:hover {
  background: #EEF0F2;
}

.tag:hover .tag__title {
  color: #000000;
}

.tag:hover .tag__descr {
  padding-left: 5px;
  color: #545353;
}

</style>
