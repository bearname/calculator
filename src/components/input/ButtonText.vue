<template>
  <button class="btn-text">{{text}}</button>
</template>

<script>
export default {
  name: "ButtonText",
  props: {
    text: {
      type: String,
      default: 'Рассчитать',
    },
  }
}
</script>

<style scoped>
.btn-text {
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 24px;
  color: #EA0029;
}

.btn-text:hover {
  color: #F53A31;
  cursor: pointer;
}

.btn-text:hover,
.btn-text:active,
.btn-text:focus {
  cursor: pointer;

}

.btn-text:active,
.btn-text:focus {
  color: #EA0029;
}
</style>
