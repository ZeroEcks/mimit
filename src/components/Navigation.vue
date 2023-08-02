<script setup lang="ts">
</script>

<template>
  <nav>
    <RouterLink to="/" class="brand">
      <img class="logo" src="https://temtem.wiki.gg/images/thumb/8/88/Mimit.png/55px-Mimit.png" />
      <span>Mimit</span>
    </RouterLink>
    <div class="menu">
      <input id="bmenub" type="checkbox" class="show">
      <label for="bmenub" class="burger pseudo button">menu</label>
      <RouterLink to="/about" class="pseudo button icon-picture">About</RouterLink>
    </div>
  </nav>
</template>
