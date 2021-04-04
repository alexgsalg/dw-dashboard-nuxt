<template>
  <header class="header" :class="{ open: sideOpen }">
    <logo classname="header_logo" />

    <div class="header_apps">
      <p class="header_apps__title">APPS</p>
      <nav>
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
        <a href="#" class="header_apps__item" exact-active-class="active">
          <calendar-icon />
          Calendário
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
  import BooksIcon from "../assets/icons/BooksIcon.vue";
  import CalendarIcon from "../assets/icons/CalendarIcon.vue";
  import EmailIcon from "../assets/icons/EmailIcon.vue";
  import TodoIcon from "../assets/icons/TodoIcon.vue";
  import Logo from "../assets/icons/Logo.vue";
  export default {
    name: "sidebar",
    components: { EmailIcon, TodoIcon, CalendarIcon, BooksIcon, Logo },
    data: () => ({
      selectValue: "areaCliente",
      sideOpen: false,
    }),
    methods: {
      selectImg: function (event) {
        this.selectValue = event.target.value;
      },
    },
  };
</script>

<style lang="scss"></style>
