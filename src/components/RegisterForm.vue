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
            input.form__input(type="text", v-model="email" required)
            label.form__label Почта
          .form__item
            input.form__input(type="text", v-model="first_name" required)
            label.form__label Имя
          .form__item
            input.form__input(type="text", v-model="last_name" required)
            label.form__label Фамилия
          .form__item
            input.form__input(type="password", v-model="password" required)
            label.form__label Пароль
          .form__item
            router-link(to="/profile") 
              button.btn.form__button Зарегистрироваться
          .form__item
            router-link(to="/login")
              a(href="#").form__link Войти
</template>

<script>
import axios from "axios";
import router from "@/router";
export default {
  name: "RegisterComponent",
  data() {
    return {
      first_name: "",
      last_name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    register() {
      axios
        .post("http://wildcherry/public/api/register", {
          email: this.email,
          password: this.password,
          first_name: this.first_name,
          last_name: this.last_name,
        })
        .then(function () {
          router.push("/login");
        })
        .catch(() => {
          console.log("ERROR");
        });
    },
  },
};
</script>

<style scoped></style>
