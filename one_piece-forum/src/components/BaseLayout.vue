<script></script>

<template>
  <div class="wrapper">
    <aside class="sidebar">
      <slot name="sidebar" />
    </aside>
    <main class="main">
      <slot name="main" />
    </main>
    <footer class="footer">
      <slot name="footer" />
    </footer>
  </div>
</template>

<style>
.sidebar {
  border: 2px solid red;
}
.main {
  border: 2px solid green;
}
.footer {
  border: 2px solid blue;
}
</style>
