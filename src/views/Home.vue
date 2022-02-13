<template>
  <h1>Предсказатель 228</h1>
  <h2>Что грозит за хранение наркотиков?</h2>
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
            <InputNumber v-model="amount" mode="decimal" suffix=" г" />
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
        <div v-if="conviction.value">
          <h3>Отбывали наказание?</h3>
          <div class="grid formgrid">
            <div class="col-12 mb-2 lg:mb-0">
              <Dropdown
                v-model="imprisonment"
                :options="imprisonmentList"
                optionLabel="name"
              />
            </div>
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
        @click="getMetaData()"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Button from "primevue/button";
import Dropdown from "primevue/dropdown";
import InputNumber from "primevue/inputnumber";
import { drugsList, sexList, regionsList } from "@/data/formValues";

export default {
  components: {
    Dropdown,
    Button,
    InputNumber,
  },
  data() {
    return {
      metadata: null,
      drug: String,
      amount: 0,
      sex: String,
      region: String,
      conviction: Boolean,
      imprisonment: Boolean,
      drugsList: [],
      sexList: [],
      regionsList: [],
      convictionList: [
        { name: "Да", value: true },
        { name: "Нет", value: false },
      ],
      imprisonmentList: [
        { name: "Да", value: true },
        { name: "Нет", value: false },
      ],
      predict: {},
    };
  },
  methods: {
    async getMetaData() {
      alert("Скоро ответим");
      const url = "http://65.108.56.20:40000/metadata";
      const response = await axios.get(url);
      console.log(response);
    },
    async getPredict() {
      const url = "http://65.108.56.20:40000/predict";
      // const payload = {};
      await axios.post(url);
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
}
h2 {
  text-align: center;
}
</style>
