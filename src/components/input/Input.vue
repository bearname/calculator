<template>
  <div class="input__wrapper">
    <label class="input__label">
      {{ text }}
    </label>
    <input :class="`${'tag' + (!error ? '': ' input__error') + (!disabled ? '': ' input__disabled')}`" class="input"
           type="text"
           :placeholder="placeholder"
           :disabled="disabled"
           :value="content"
           @input="updateInput"
    >
  </div>
</template>

<script>
export default {
  name: "Input",
  model: {
    prop: 'modelValue',
    event: 'input'
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
    text: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: '',
    },
  },
  emits: ['change'],
  data () {
    return {
      error: false,
      content: this.value
    }
  },
  methods: {
    updateInput (event) {
      const value = event.target.value;
      this.content = value;
      this.$emit('input', value)
    },
  }
}
</script>

<style scoped>
.input__wrapper {
  min-width: 288px;
  width: 100%;
}

.input {
  border: 1px solid #DFE3E6;
  box-sizing: border-box;
  border-radius: 3px;
  height: 40px;
  width: 288px;
  padding: 8px 10px;
  transition: all 0.2s ease-in-out;
}

.input:hover {
  border: 1px solid #000000;
}

.input::placeholder,
.input__label {
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 24px;
}

.input::placeholder {
  color: #BEC5CC;
}

.input:focus,
.input:focus-visible {
  outline: none;
}

.input:focus::placeholder {
  color: #000000;
}


.input__disabled {
  border: 1px solid #808080;
}

.input__disabled::placeholder {
  color: #808080;
}

.input__error {
  border: 1px solid #ea0029;
}

.input__label {
  display: block;
  color: #000000;
  margin-bottom: 8px;
  text-align: left;
}

</style>
