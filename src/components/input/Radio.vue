<template>
  <label :class="`${'tag' + (!isChecked ? '': ' tag__active')}`">
    <input class="tag__checkbox" type="radio" :value="value" :name="name" v-model="radioButtonValue">
    <span>{{ label }}</span>
  </label>
</template>

<script>
export default {
  name: 'Radio',
  props: ['name', 'label', 'value', 'modelValue'],
  computed: {
    radioButtonValue: {
      get: function () {
        return this.value
      },
      set: function () {

        this.$emit("update:modelValue", this.value)
      }
    },
    isChecked () {
      return this.modelValue === this.value;
    }
  }
}
</script>


<style scoped>
.tag {
  position: relative;
  padding: 6px 12px;
  border-radius: 50px;
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 24px;
  text-align: center;
  background: #EEF0F2;
}

.tag__checkbox {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
}

.tag__checkbox:hover {
  cursor: pointer;
}

.tag .tag__title {
  color: #000000;
}

.tag .tag__description {
  padding-left: 5px;
  color: #545353;
}


.tag:hover {
  background: #EEF0F2;
  color: black;
  cursor: pointer;
}

.tag__active,
.tag__active:hover,
.tag__clicked {
  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  color: #FFFFFF;
}

.tag__active .tag__title,
.tag__active .tag__description {
  color: #FFFFFF;
}

.tag__clicked .tag__title,
.tag__clicked .tag__description {
  color: #FFFFFF;
}

.tag__active:hover {
  opacity: 0.9;
}

.tag:hover .tag__title {
  color: #000000;
}

.tag:hover .tag__description {
  padding-left: 5px;
  color: #545353;
}

</style>

