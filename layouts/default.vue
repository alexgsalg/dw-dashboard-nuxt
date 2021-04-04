<template>
  <div id="app">
    <SideBar />

    <main class="main-content">
      <TopBar />
      <vue-page-transition name="fade">
        <!-- <router-view/> -->
        <Nuxt />
      </vue-page-transition>
    </main>
  </div>
</template>

<style lang="scss">
@import url('https://use.fontawesome.com/releases/v5.15.3/css/all.css');
</style>
