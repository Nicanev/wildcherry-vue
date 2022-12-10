<template lang="pug">
main.main
  .auth
    .auth__container
      .auth__body
        .auth__img
          img(src="@/assets/img/icons/ID.png", alt="WILDCHERRY ID")
        .auth__title
          h2 Регистрация
        .auth__form.form
          .form__item
            input.form__input(type="text", required)
            label.form__label Почта
          .form__item
            input.form__input(type="text", required)
            label.form__label Имя
          .form__item
            input.form__input(type="text", required)
            label.form__label Фамилия
          .form__item
            input.form__input(type="password", required)
            label.form__label Пароль
          .form__item
            router-link(to="/profile") 
              button.btn.form__button Зарегистрироваться
          .form__item
            router-link(to="/login")
              a(href="#").form__link Войти
</template>

<script>
export default {
  name: "RegisterComponent",
};
</script>

<style scoped></style>
