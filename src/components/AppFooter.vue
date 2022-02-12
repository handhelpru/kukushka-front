<template>
  <div class="layout-footer">
    <div class="layout-footer-left">
      <span
        >Создано на хакатоне
        <a href="https://projector2022.te-st.ru">Прожектор-2022</a>
        командой <a href="https://hand-help.ru">hand-help.ru</a>
      </span>
    </div>

    <div class="layout-footer-right">
      <a href="https://github.com/handhelpru/kukushka" class="mr-3">
        <i class="pi pi-github"></i>
      </a>
    </div>
  </div>
</template>

<style lang="css" scoped>
.layout-footer {
  font-size: 1rem;
  padding: 2rem;
  background-color: var(--surface-card);
  display: flex;
  align-items: center;
  justify-content: space-between;
}
a {
  color: var(--text-color);
  font-weight: 600;
}

.layout-footer-right a {
  color: var(--text-secondary-color);
  font-size: 1.5rem;
}
</style>
