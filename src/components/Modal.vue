<template>
  <div class="modal-mask">
    <div class="modal-wrapper" @click="$emit('close')"></div>
    <div class="modal-container">
      <div class="modal-body-wrapper">
        <div class="modal__close" @click="$emit('close')">
          <CloseIcon/>
        </div>
        <div class="modal-header">
          <slot name="header">
            default header
          </slot>
        </div>

        <div class="modal-body">
          <slot name="body">
            default body
          </slot>
        </div>

        <div class="modal-footer">
          <slot name="footer">
            <!--            default footer-->
            <Button :text="'Добавить'" @click="$emit('close')"/>
            <!--            <button class="modal-default-button" @click="$emit('close')">-->
            <!--              OK-->
            <!--            </button>-->
          </slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "./input/Button";
import CloseIcon from "./icons/CloseIcon";

export default {
  name: "Modal",
  components: { CloseIcon, Button }
}
</script>

<style>


.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.3);
  display: table;
}

.modal-wrapper {
  width: 100%;
  height: 100%;
  position: absolute;
}

.modal-container {
  margin: 0 auto;
  background: #FFFFFF;
  max-width: 552px;
  width: 100%;
  border-radius: 30px;
  position: absolute;
  top: 120px;
  left: 50%;
  transform: translateX(-50%);
}

.modal-body-wrapper {
  padding: 32px;
}

.modal__close {
  position: absolute;
  top: 27px;
  right: 27px;
  cursor: pointer;
}

.modal-header h3 {
  margin-top: 0;
}

.modal__description {
  padding-right: 50px;
}

.modal-body {
  margin: 20px 0;
}

.modal-default-button {
  display: block;
  margin-top: 1rem;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.5s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

@media all and (max-width: 1440px) {
  .modal-container {
    max-width: 453px;
    width: 100%;
  }
}

/*mobile*/
@media all and (max-width: 768px) {
  .modal-container {
    max-width: unset;
    width: 100%;
    top: 0;
    border-radius: 0;
    height: 100%;
  }

  .modal-body-wrapper {
    height: 100vh;
    padding: 16px;
  }
  .modal__close {
    top: 16px;
    right: 16px;
  }

  .modal-footer {
    position: absolute;
    bottom: 0;
    width: calc(100% - 32px);
    left: 0;
    padding: 16px;
  }
}

</style>
