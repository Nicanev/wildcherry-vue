<script setup>
import TheHeader from "@/components/TheHeader";
import TheFooter from "@/components/TheFooter";
</script>

<template>
  <div class="wrapper">
    <TheHeader />
    <router-view />
    <TheFooter />
  </div>
</template>

<style lang="scss"></style>
