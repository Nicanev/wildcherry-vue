<template>
  <div class="profile">
    <div class="profile__container">
      <div class="profile__title">Личный кабинет</div>
      <div class="profile__block">
        <button class="profile__exit" @click="exit">Выйти</button>
        <div class="profile__name">{{ first_name }} {{ last_name }}</div>
        <div class="profile__info">
          <div class="profile__email profile__data">
            <span>Email</span> {{ email }}
          </div>
          <div class="profile__role profile__data">
            <span>Роль</span> Покупатель
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.profile {
  &__title {
    font-size: 2.4rem;
    font-weight: bold;
    margin-bottom: 2rem;
  }
  &__block {
    position: relative;
    width: 100%;
    border-radius: 1.5rem;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    padding: 2.5rem;
  }
  &__exit {
    position: absolute;
    z-index: 100;
    background-color: transparent;
    border: none;
    font-size: 1.6rem;
    text-decoration: underline dotted;
    color: #242734;
    top: 2.5rem;
    right: 2.5rem;
    width: max-content;
    height: max-content;
    cursor: pointer;
  }
  &__info {
    display: flex;
    gap: 5rem;
  }
  &__name {
    margin-bottom: 3rem;
    font-size: 2rem;
    font-weight: bold;
  }
  &__data {
    display: flex;
    flex-direction: column;
    font-size: 1.6rem;
    gap: 0.5rem;
    span {
      font-size: 1.4rem;
      color: #a0949b;
    }
  }
}
</style>

<script>
import router from "@/router";
export default {
  mounted() {
    if (!this.$cookies.get("token")) {
      router.push("/login");
    }
  },
  data() {
    return {
      email: this.$cookies.get("email"),
      first_name: this.$cookies.get("first_name"),
      last_name: this.$cookies.get("last_name"),
    };
  },
  methods: {
    exit() {
      this.$cookies.remove("token");
      this.$cookies.remove("email");
      this.$cookies.remove("first_name");
      this.$cookies.remove("last_name");
      location.reload();
    },
  },
};
</script>
