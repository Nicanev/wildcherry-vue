<template lang="pug">
main.main
  .auth
    .auth__container
      .auth__body
        .auth__img
          img(src="@/assets/img/icons/ID.png", alt="WILDCHERRY ID")
        .auth__title
          h2 Вход в аккаунт
        .auth__form.form
          .form__item
            input.form__input(type="text", required)
            label.form__label Логин
          .form__item
            input.form__input(type="password", required)
            label.form__label Пароль
          .form__item
            button.btn.form__button Войти в аккаунт
          .form__item
            a(href="#").form__link Регистрация
</template>

<script>
export default {
  name: "LoginComponent",
};
</script>

<style scoped></style>
