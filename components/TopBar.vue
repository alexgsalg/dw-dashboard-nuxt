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
        <a class="admin-icons__item">
          <img src="../assets/img/icon-bell.svg" alt="íconde de notificação" />
          <ul class="notification_dropdown">
            <li>
              <p>Novo curso disponível</p>
              <span>X</span>
            </li>
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
}
</script>

<style lang="scss"></style>
