<template>
  <div class="actionBar">
    <h1 class="actionBar__title">{{ title }}</h1>
    <div class="actionBar__breadcrumbs">
      <a href="#" class="breadcrumb_tohome">
        <home-icon />
      </a>
      <img src="../assets/img/breadcrumbs-arrow.png" alt="breadcrumbs" />
      <p>Cursos</p>
    </div>
    <a href="#" class="actionBar__config">
      <config-neg-icon />
    </a>
  </div>
</template>

<script>
import ConfigNegIcon from "../assets/icons/ConfigNegIcon.vue";
import HomeIcon from "../assets/icons/HomeIcon.vue";
export default {
  components: { HomeIcon, ConfigNegIcon },
  name: "ActionBar",
  props: ["title"],
};
</script>

<style></style>
