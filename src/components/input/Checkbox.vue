<template>
  <label class="container">
    {{label}}
    <input
        type="checkbox" :value="val" v-model="model"
        :disabled="disabled"
    >
    <span class="checkmark"></span>
  </label>
</template>

<script>

export default {
  name: "Checkbox",
  props: {
    val: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    text: {
      type: String,
      default: ''
    },
    modelValue: {
      type: Array,
      required: true
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  emits: ['update:modelValue'],
  computed: {
    model: {
      get() {
        return this.modelValue
      },
      set(value) {
        this.$emit('update:modelValue', value)
      }
    }
  },
}
</script>

<style scoped>
.container {
  display: block;
  position: relative;
  width: 20px;
  height: 20px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 20px;
  width: 20px;
  background: #FFFFFF;

  border: 1px solid #DFE3E6;
  box-sizing: border-box;
  border-radius: 6px;
  transition: all 0.2s ease-in-out;
}

.container:hover input ~ .checkmark {
  background: #FFFFFF;
  /* Black 000 */

  border: 1px solid #000000;
  box-sizing: border-box;
  border-radius: 6px;
}

.container input:checked ~ .checkmark {
  background: linear-gradient(
      255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  border-radius: 6px;
}


.container input[disabled] ~ .checkmark {
  background: #BEC5CC;
  border: 1px solid #BEC5CC;
  box-sizing: border-box;
  border-radius: 6px;
}

.container input[disabled] ~ .checkmark:after {
  display: block;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.container input:checked ~ .checkmark:after {
  display: block;
}

.container .checkmark:after {
  left: 6px;
  top: 3px;
  width: 4px;
  height: 8px;
  border: solid white;
  border-width: 0 2px 2px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>
