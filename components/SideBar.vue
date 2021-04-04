<template>
  <header class="header" :class="{ open: sideOpen }">
    <logo classname="header_logo" />

    <div class="header_apps">
      <p class="header_apps__title">APPS</p>
      <nav>
        <router-link
          to="/"
          class="header_apps__item"
          exact-active-class="active"
        >
          <home-icon />
          Home
        </router-link>
        <router-link
          to="/cursos"
          class="header_apps__item"
          exact-active-class="active"
        >
          <books-icon />
          Cursos
        </router-link>

        <router-link
          to="/emails"
          class="header_apps__item"
          exact-active-class="active"
        >
          <email-icon />
          Email
        </router-link>

        <a href="#" class="header_apps__item" exact-active-class="active">
          <todo-icon />
          Todos
        </a>
      </nav>
    </div>

    <!-- Cabeçalho mobile -->
    <div class="section_mobile">
      <logo classname="mobile_logo" />
      <button id="menu" @click="sideOpen = !sideOpen">
        <i class="fas fa-bars"></i>
      </button>
    </div>
  </header>
</template>

<script>
import BooksIcon from '../assets/icons/BooksIcon.vue'
import HomeIcon from '../assets/icons/HomeIcon.vue'
import EmailIcon from '../assets/icons/EmailIcon.vue'
import TodoIcon from '../assets/icons/TodoIcon.vue'
import Logo from '../assets/icons/Logo.vue'
export default {
  name: 'Sidebar',
  components: { EmailIcon, TodoIcon, BooksIcon, HomeIcon, Logo },
  data: () => ({
    selectValue: 'areaCliente',
    sideOpen: false,
  }),
  methods: {
    selectImg(event) {
      this.selectValue = event.target.value
    },
  },
}
</script>

<style lang="scss"></style>
