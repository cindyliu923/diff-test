<script>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home/</RouterLink>
        <RouterLink to="/diff">Diff</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
