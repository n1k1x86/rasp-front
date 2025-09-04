<script>
    import { onMount } from "svelte";
    import { page } from '$app/stores';
  
    let dark = false;
  
    onMount(() => {
      dark = localStorage.getItem("theme") === "dark";
      applyTheme();
    });
  
    function toggleTheme() {
      dark = !dark;
      localStorage.setItem("theme", dark ? "dark" : "light");
      applyTheme();
    }
  
    function applyTheme() {
      if (typeof document !== "undefined") {
        document.documentElement.classList.toggle("dark", dark);
      }
    }
  </script>
  
  <style>
    :global(:root) {
      --bg: #ffffff;
      --fg: #000000;
      --card-bg: #f3f3f3;
      --accent: #4f46e5;
    }
  
    :global(.dark) {
      --bg: #121212;
      --fg: #e5e5e5;
      --card-bg: #1e1e1e;
      --accent: #6366f1;
    }
  
    :global(body) {
      margin: 0;
      font-family: system-ui, sans-serif;
      background: var(--bg);
      color: var(--fg);
    }
  
    .layout {
      display: grid;
      grid-template-columns: 200px 1fr;
      height: 100vh;
    }
  
    nav {
      background: var(--card-bg);
      display: flex;
      flex-direction: column;
      padding: 1rem;
    }
  
    nav a {
      color: var(--fg);
      text-decoration: none;
      margin-bottom: 1rem;
      padding: 0.5rem;
      border-radius: 8px;
    }
  
    nav a.active,
    nav a:hover {
      background: var(--accent);
      color: #fff;
    }
  
    main {
      padding: 1.5rem;
    }
  
    .theme-btn {
      margin-top: auto;
      padding: 0.5rem;
      cursor: pointer;
      border: none;
      border-radius: 8px;
      background: var(--accent);
      color: #fff;
    }
  </style>
  
  
  <div class="layout">
    <nav>
      <h2>RASP Admin</h2>
  
      <!-- Используем $page напрямую -->
      <a href="/" class:active={$page.url.pathname === "/"}>📊 Dashboard</a>
      <a href="/agents" class:active={$page.url.pathname.startsWith("/agents")}>🖥️ Агенты</a>
      <a href="/logs" class:active={$page.url.pathname.startsWith("/logs")}>📜 Логи</a>
      <a href="/settings" class:active={$page.url.pathname.startsWith("/settings")}>⚙️ Настройки</a>
  
      <button class="theme-btn" on:click={toggleTheme}>
        {#if dark}🌙 Тёмная{:else}☀️ Светлая{/if}
      </button>
    </nav>
  
    <main>
      <slot />
    </main>
  </div>
  