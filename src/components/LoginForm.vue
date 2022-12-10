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
            input.form__input(type="text", v-model="email" required)
            label.form__label Почта
          .form__item
            input.form__input(type="password", v-model="password" required)
            label.form__label Пароль
          .form__item
            button.btn.form__button(@click="signIn") Войти в аккаунт
          .form__item
            router-link(to="/register")
              a(href="#").form__link Регистрация
</template>

<script>
import axios from "axios";
export default {
  name: "LoginComponent",
  data() {
    return {
      email: "",
      password: "",
      error: false,
    };
  },
  methods: {
    signIn() {
      let cookie = this.$cookies;
      axios
        .post("http://wildcherry/public/api/login", {
          email: this.email,
          password: this.password,
        })
        .then(function (response) {
          cookie.set("first_name", response.data.first_name);
          cookie.set("last_name", response.data.last_name);
          cookie.set("email", response.data.email);
          cookie.set("token", response.data.token);
          location.reload();
        })
        .catch(() => {
          this.error = true;
          console.log("ERROR");
        });
    },
  },
};
</script>

<style scoped></style>
