<template>
  <h1>Предсказатель 228</h1>
  <p class="center">Протототип</p>
  <h2>Узнайте, что грозит за хранение наркотиков</h2>
  <div class="flex justify-content-center m-5">
    <Accordion>
      <AccordionTab header="Как это работает?">
        <p>
          Предсказатель анализирует приговоры и дает прогноз по статье 228 УК в
          суде первой инстанции. Исход дела зависит от от региона, пола
          подсудимого, количества наркотика, признания вины и наличия судимости
        </p>
      </AccordionTab>
    </Accordion>
  </div>
  <div class="grid flex justify-content-center">
    <div class="col-6 md:col-6 p-fluid flex justify-content-center">
      <div class="card">
        <h3>Какой наркотик?</h3>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:mb-0">
            <Dropdown v-model="drug" :options="drugsList" optionLabel="name" />
          </div>
        </div>
        <h3>Количество (в граммах)</h3>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:mb-0">
            <InputNumber v-model="amount" mode="decimal" suffix=" г" :min="0" />
          </div>
        </div>
        <h3>Пол</h3>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:mb-0">
            <Dropdown v-model="sex" :options="sexList" optionLabel="name" />
          </div>
        </div>
        <h3>Регион (Москвы пока нет)</h3>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:mb-0">
            <Dropdown
              v-model="region"
              :options="regionsList"
              optionLabel="name"
            />
          </div>
        </div>
        <h3>Есть ли судимость?</h3>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:mb-0">
            <Dropdown
              v-model="conviction"
              :options="convictionList"
              optionLabel="name"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="grid flex justify-content-center m-5">
    <div class="p-fluid flex justify-content-center">
      <Button
        label="Узнать прогноз"
        class="p-button-lg"
        @click="getPredict()"
      />
    </div>
  </div>
  <div class="flex justify-content-center m-5">
    <Prediction v-if="prediction.scenario_id" :prediction="prediction" />
  </div>
</template>

<script>
import axios from "axios";
import Button from "primevue/button";
import Dropdown from "primevue/dropdown";
import InputNumber from "primevue/inputnumber";
import { drugsList, sexList, regionsList } from "@/data/formValues";
import Prediction from "@/components/Prediction";
import Accordion from "primevue/accordion";
import AccordionTab from "primevue/accordiontab";

export default {
  components: {
    Dropdown,
    Button,
    InputNumber,
    Prediction,
    Accordion,
    AccordionTab,
  },
  data() {
    return {
      metadata: null,
      drug: String,
      amount: 0,
      sex: String,
      region: String,
      conviction: Boolean,
      drugsList: [],
      sexList: [],
      regionsList: [],
      convictionList: [
        { name: "Да", value: true },
        { name: "Нет", value: false },
      ],
      prediction: {},
    };
  },
  methods: {
    async getPredict() {
      const url = `${process.env.VUE_APP_API_HOST}/predict`;
      const payload = {
        sex: this.sex.name,
        region: this.region.name,
        drug: this.drug.name,
        drug_amount: this.amount,
        conviction: this.conviction.value,
      };
      await axios.post(url, payload).then((response) => {
        this.prediction = response.data;
      });
    },
  },
  mounted() {
    this.drugsList = drugsList;
    this.sexList = sexList;
    this.regionsList = regionsList;
  },
};
</script>
<style scoped>
h1 {
  text-align: center;
  font-size: 60px;
  margin-top: 60px;
  margin-bottom: 10px;
}
h2 {
  text-align: center;
}
p {
  text-align: center;
  margin-top: 0px;
  margin-bottom: 20px;
}
</style>
