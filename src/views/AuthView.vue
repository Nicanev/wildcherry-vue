<template>
  <LoginForm v-if="this.$route.name === 'login'" />
  <RegisterForm v-if="this.$route.name === 'register'" />
</template>

<script setup>
import LoginForm from "@/components/LoginForm.vue";
import RegisterForm from "@/components/RegisterForm.vue";
</script>

<script>
import router from "@/router";
export default {
  mounted() {
    if (this.$cookies.get("token")) {
      router.push("/profile");
    }
  },
};
</script>
