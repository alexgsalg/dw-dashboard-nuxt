<template>
  <div class="actionBar">
    <h1 class="actionBar__title">{{ title }}</h1>
    <div class="actionBar__breadcrumbs">
      <router-link to="/" class="breadcrumb_tohome">
        <home-icon />
      </router-link>
      <img src="../assets/img/breadcrumbs-arrow.png" alt="breadcrumbs" />
      <p>Cursos</p>
    </div>
    <a href="#" class="actionBar__config">
      <config-neg-icon />
    </a>
  </div>
</template>

<script>
import ConfigNegIcon from '../assets/icons/ConfigNegIcon.vue'
import HomeIcon from '../assets/icons/HomeIcon.vue'
export default {
  name: 'ActionBar',
  components: { HomeIcon, ConfigNegIcon },
  props: { title: { default: 'Dashboard DW', type: String } },
}
</script>

<style></style>
