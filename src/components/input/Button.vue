<template>
  <button :class="`${'btn' + (disabled ? ' btn-disabled': '')}`">{{ text }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    text: {
      type: String,
      default: '',
    },
  }
}
</script>

<style>

/*desktop*/
.btn {
  display: block;
  width: 100%;
  min-width: 288px;

  height: 56px;

  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
  box-shadow: 0 0 24px rgba(234, 0, 41, 0.33);
  border-radius: 6px;

  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  text-align: center;

  color: #FFFFFF;

  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

.btn:hover,
.btn:focus {
  background: #EA0029;
  box-shadow: 0 0 24px rgba(234, 0, 41, 0.33);
  border-radius: 6px;
}

.btn-disabled {
  background: #BEC5CC;
  border-radius: 6px;
}

.btn-disabled:hover {
  background: #BEC5CC;
  border-radius: 6px;
  opacity: 0.9;
}

.btn-secondary {
  font-family: 'Lab Grotesque', Arial, sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  border: 1px solid white;

  text-align: center;

  color: #FFFFFF;
}

.btn-secondary:hover {
  background: white;
  color: #000000;
}

.btn-secondary-disabled,
.btn-secondary-disabled:hover{
  background: #BEC5CC;
  border-radius: 6px;
  color: #FFFFFF;
  border: none;
}

.btn-secondary-disabled:hover {
  opacity: 0.9;
}

/*tablet*/
@media all and (max-width: 1440px) {

}

/*mobile*/
@media all and (max-width: 768px) {
  .btn {
    min-width: 288px;
    height: 40px;

    background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;
    box-shadow: 0 0 24px rgba(234, 0, 41, 0.33);
    border-radius: 6px;

    font-size: 12px;
    line-height: 16px;

    color: #FFFFFF;
  }

  .btn-disabled {
    background: #BEC5CC;
    border-radius: 6px;
  }

  .btn-secondary {
    width: 158px;
    height: 40px;
  }

  .btn-secondary-disabled,
  .btn-secondary-disabled:hover{
    background: #BEC5CC;
    border-radius: 6px;
    color: #FFFFFF;
    border: none;
  }

  .btn-secondary-disabled:hover {
    opacity: 0.9;
  }

}
</style>
