<template>
  <h1>Предсказатель 228</h1>
  <div class="grid flex justify-content-center">
    <div class="col-6 md:col-6 p-fluid flex justify-content-center">
      <div class="card">
        <h2>В чем обвиняют?</h2>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:col-4 lg:mb-0">
            <Dropdown />
          </div>
        </div>
        <h2>Какой наркотик?</h2>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:col-4 lg:mb-0">
            <Dropdown />
          </div>
        </div>
        <h2>Количество (в граммах)</h2>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:col-4 lg:mb-0">
            <Dropdown />
          </div>
        </div>
        <h2>Пол</h2>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:col-4 lg:mb-0">
            <Dropdown />
          </div>
        </div>
        <h2>Регион (Москвы пока нет)</h2>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:col-4 lg:mb-0">
            <Dropdown />
          </div>
        </div>
        <h2>Есть ли судимость?</h2>
        <div class="grid formgrid">
          <div class="col-12 mb-2 lg:col-4 lg:mb-0">
            <Dropdown />
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="grid flex justify-content-center m-5">
    <div class="col-4 md:col-4 p-fluid flex justify-content-center">
      <Button label="Узнать прогноз" class="p-button-lg" />
    </div>
  </div>
</template>

<script>
import Button from "primevue/button";
import Dropdown from "primevue/dropdown";

export default {
  components: {
    Dropdown,
    Button,
  },
};
</script>
<style scoped>
h1 {
  text-align: center;
  font-size: 60px;
  margin-top: 60px;
}
</style>
