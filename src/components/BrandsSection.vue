<template lang="pug">
section.brands
  .brands__container
    .brands__title
      | Популярные бренды
      a(href="#")  Смотреть все
    .brands__category.category
      ul.category__list
        li.category__item
          button.btn Женщинам
        li.category__item
          button.btn Мужчинам
        li.category__item
          button.btn Детям
        li.category__item
          button.btn Обувь
        li.category__item
          button.btn Ассексуары
        li.category__item
          button.btn Электроника
    ul.brands__list
      li.brands__item
        img(src="@/assets/img/brands/xiaomi.png", alt="Brand")
      li.brands__item
        img(src="@/assets/img/brands/jbl.png", alt="Brand")
      li.brands__item
        img(src="@/assets/img/brands/Adidas.png", alt="Brand")
</template>

<script>
export default {
  name: "BrandsSection",
};
</script>

<style scoped></style>
