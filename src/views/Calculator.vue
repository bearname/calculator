<template>
  <div>
    <div v-if="showModal === false" class="bg">
      <div class="block-center">
        <button class="btn btn-secondary" @click="showModal = true">Налоговый вычет</button>
      </div>
      <Button v-show="false"/>
    </div>
    <!--    <button id="show-modal" @click="showModal = true">Show Modal</button>-->
    <!-- use the modal component, pass in the prop -->
    <transition name="modal">
      <Modal v-show="showModal" @close="showModal = false">
        <!--
          you can use custom content here to overwrite
          default content
        -->
        <template v-slot:header>
          <h3>Налоговый вычет</h3>
        </template>
        <template v-slot:body>
          <p class="modal__description"> Используйте налоговый вычет чтобы погасить ипотеку досрочно.
            Размер налогового вычета составляет не более 13% от своего официального годового дохода.</p>
          <div class="spacer"></div>
          <BaseInput
              id="email"
              class="mb-4"
              type="email"
              label="Цена квартиры"
              placeholder="цена"
              v-model="price"
              :model-value="price"
          />
          <div class="spacer-sm"></div>
          <BaseInput
              id="email"
              class="mb-4"
              type="email"
              label="Ваша зарплата в месяц"
              placeholder="Введите данные"
              v-model="salary"
          />

          <div class="spacer-sm"></div>
          <ButtonText @click="calculate"/>
          <div class="spacer"></div>
          <div v-if="isShowResult" class="result--wrapper">
            <p class="caption">Итого можете внести в качестве досрочных:</p>
            <div v-for="(price, index) in results" v-bind:key="index">
              <p class="flex" style="padding: 16px 0; border-bottom: 1px solid #DFE3E6;">
                <Checkbox class="mr-10"/>
                <span class="mr-10" style="color:black">{{ price }} рублей </span> в {{ index + 1 }} год
              </p>
            </div>
          </div>
          <div class="spacer"></div>

          <div class="wrapper">
            <span class="caption">Что уменьшаем?</span>
            <div class="flex">
              <div class="mr-10">
                <label><input type="radio" id="huey" name="drone" value="0" v-model="MySelectedValues"
                              checked> Платеж</label>
              </div>

              <div>
                <label class=""><input type="radio" id="dewey" name="drone" value="1" v-model="MySelectedValues">
                  Срок</label>
              </div>
            </div>
          </div>
        </template>
      </Modal>
    </transition>
  </div>
</template>

<script>
import Button from "../components/input/Button";
import Modal from "../components/Modal";
import ButtonText from "../components/input/ButtonText";
import BaseInput from "../components/input/BaseInput";
import Checkbox from "../components/input/Checkbox";

export default {
  name: "Calculator",
  components: { Checkbox, BaseInput, ButtonText, Modal, Button },
  data () {
    return {
      showModal: false,
      price: 2000000,
      salary: '',
      MySelectedValues: 0,
      isShowResult: false,
      results: [],
    }
  },
  methods: {
    toggled () {
      this.showModal = false;
    },
    calculate () {
      let maxTaxDeduction = 0;
      if (this.price < 2000000) {
        maxTaxDeduction = this.price * 0.13;
      } else {
        maxTaxDeduction = 260000;
      }
      if (this.salary.length <= 3) {
        return;
      }
      this.results = [];
      let payByMonth = (this.salary * 12) * 0.13;
      for (let repaid = 0; repaid < maxTaxDeduction;) {
        let pay = ((maxTaxDeduction - repaid) > payByMonth) ? payByMonth : maxTaxDeduction - repaid;
        this.results.push(pay);
        repaid += pay;
      }
      this.isShowResult = true;
    }
  },
}
</script>

<style scoped>
.bg {
  width: 100vw;
  min-height: 100vh;
  height: 100%;

  background: linear-gradient(255.35deg, #DC3131 0.83%, rgba(255, 79, 79, 0) 108.93%), #FF5E56;

  box-shadow: 0 -0.11px 16.9495px rgba(183, 187, 225, 0.33);
  border-radius: 0;
}

.block-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.result--wrapper {
  height: 300px;
  overflow-y: scroll;
}
</style>
