<template>
  <div class="topBar">
    <nav class="topBar_icons">
      <a href="#" class="topBar_icons__item">
        <img src="../assets/img/icon-todo.svg" alt="íconde de todo" />
      </a>
      <a href="#" class="topBar_icons__item">
        <img src="../assets/img/icon-chat.svg" alt="íconde de conversa" />
      </a>
      <a href="#" class="topBar_icons__item">
        <img src="../assets/img/icon-mail.svg" alt="íconde de email" />
      </a>
      <a href="#" class="topBar_icons__item">
        <img src="../assets/img/icon-calendar.svg" alt="íconde de email" />
      </a>
      <a href="#" class="topBar_icons__item star-icon">
        <img src="../assets/img/icon-star.svg" alt="íconde de star" />
      </a>
    </nav>
    <div class="topBar_admin">
      <nav class="admin-icons">
        <a
          class="admin-icons__item"
          @click="notificationBox = !notificationBox"
        >
          <img src="../assets/img/icon-bell.svg" alt="íconde de notificação" />
          <ul v-if="notificationBox == true" class="notification_dropdown">
            <li>
              <p>Novo curso de Programação responsiva disponível</p>
            </li>
            <button class="notification_dropdown__btn">
              Limpar notificações
            </button>
          </ul>
        </a>
      </nav>
      <div class="admin_user">
        <div>
          <p class="admin_user__name">Maria Elza</p>
          <p class="admin_user__group">Cliente VIP</p>
        </div>
        <div class="admin_user__avatar">
          <img src="../assets/img/Avatar.png" alt="Avatar" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ActionBar',
  components: {},
  data: () => ({
    notificationBox: false,
  }),
}
</script>

<style lang="scss"></style>
