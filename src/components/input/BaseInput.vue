<template>
  <div class="input__wrapper">
    <label v-if="label" :for="id" class="input__label">
      {{ label }}
    </label>
    <input
        :class="`${'tag' + (!error ? '': ' input__error') + (!disabled ? '': ' input__disabled')}`" class="input"
        :id="id"
        :type="type"
        :value="modelValue"
        @input="updateInput"
        :placeholder="placeholder"
        autocomplete="off"
    />
  </div>
</template>

<script>
export default {
  name: "BaseInput",
  props: {
    id: {
      type: String,
      default: "",
    },
    label: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    type: {
      type: String,
      default: "text",
    }
  },
  data (props) {
    return {
      error: false,
      disabled: false,
      tempValue: props.value,
    }
  },
  methods: {
    updateInput (event) {
      const value = event.target.value;

      const isNumber = /^\d+$/.test(value);
      if (!isNumber) {
        this.error = true;
        return;
      }
      this.error = false;
      this.$emit("update:modelValue", value);
    }
  }
};
</script>

<style scoped>
.input__wrapper {
  width: 100%;
  min-width: 288px;
}

.input {
  border: 1px solid #DFE3E6;
  box-sizing: border-box;
  border-radius: 3px;
  height: 40px;
  width: 100%;
  min-width: 288px;
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
