<template>
  <div class="accordion-container">
    <div class="wrapper">
      <div class="row">
        <div class="accordion">
          <details class="accordion__item">
            <summary class="accordion__title">Часто задаваемые вопросы.</summary>
            <p class="accordion__content">Почему у верблюда два горба?</p>
          </details>
          <details class="accordion__item">
            <summary class="accordion__title">Часто задаваемые вопросы.</summary>
            <p class="accordion__content">Почему у верблюда два горба?</p>
          </details>
          <details class="accordion__item">
            <summary class="accordion__title">Часто задаваемые вопросы.</summary>
            <p class="accordion__content">Почему у верблюда два горба?</p>
          </details>
          <details class="accordion__item">
            <summary class="accordion__title">Часто задаваемые вопросы.</summary>
            <p class="accordion__content">Почему у верблюда два горба?</p>
          </details>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Accordion"
};
</script>

<style lang="scss" scoped>
// отключили стрелочку
summary::-webkit-details-marker {
  display: none;
}
.wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.accordion {
  max-width: 320px;
  box-shadow: 0 0 12px 4px rgba(0, 0, 0, 0.4);
  border-radius: 8px;
  overflow: hidden;

  &__item {
    background-color: #353535;
    color: #ffffff;
  }

  &__title {
    width: 100%;
    text-align: center;
    font-size: 20px;
    background-color: #272727;
    outline: none;
    cursor: pointer;
    border-bottom: 1px solid #777;
    padding: 10px 40px 10px 10px;
    transition: 0.3s all;
    position: relative; // позволяет абсолютно спозиционировать ::after
  }

  &__title:hover {
    background-color: #111;
  }

  &__title::after {
    display: block;
    content: "▼";
    font-size: 12px;
    position: absolute;
    right: 12px;
    top: 50%;
    transform: translateY(-50%);
    transition: 0.3s all;
  }

  &__content {
    padding: 20px;
    margin: 0;
  }
}
// смена направления треугольничка
// use "open" отслеживание состояния тега
.accordion__item[open] .accordion__title::after {
  transform: translateY(-50%) rotate(180deg);
}
// коррекция закругления
.accordion__item:not([open]):last-child .accordion__title {
  border-bottom: 1px solid transparent; // делаем прозрачным
}
</style>