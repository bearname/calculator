<template>
  <div>
    <div v-if="showModal === false" class="bg">
      <div class="block-center">
        <button class="btn btn-secondary" @click="showModal = true">Налоговый вычет</button>
      </div>
      <Button v-show="false"/>
    </div>
    <transition name="modal">
      <Modal v-show="showModal" @close="showModal = false">
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
                <Checkbox :val="index"
                          v-model="componentSelectedItems"
                          :model-value="componentSelectedItems"
                          class="mr-10"/>
                <span class="mr-10" style="color:black">{{ price }} рублей </span> в {{ index + 1 }} год
              </p>
            </div>
          </div>
          <div class="spacer"></div>

          <div class="wrapper flex">
            <span class="caption pt-7 mr-10">Что уменьшаем?</span>
            <div class="flex">
              <Radio class="mr-10" name="options" v-model="MySelectedValue" :value="1" :model-value="MySelectedValue" label="Платеж"/>
              <Radio name="options" v-model="MySelectedValue" :value="2" :model-value="MySelectedValue" label="Срок"/>
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
import Radio from "../components/input/Radio";

export default {
  name: "Calculator",
  components: { Radio, Checkbox, BaseInput, ButtonText, Modal, Button },
  data () {
    return {
      showModal: false,
      price: 2000000,
      salary: '',
      MySelectedValues: 0,
      MySelectedValue: 1,
      isShowResult: false,
      results: [],
      componentSelectedItems: [],
    }
  },
  methods: {
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

  box-shadow: 0 -0.11px 17px rgba(183, 187, 225, 0.33);
  border-radius: 0;
}

.block-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.result--wrapper {
  height: 252px;
  overflow-y: scroll;
}
</style>
