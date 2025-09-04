<script>
  import { onMount } from "svelte";

  let dark = false;

  onMount(() => {
    // проверить сохранённую тему
    dark = localStorage.getItem("theme") === "dark";
    updateTheme();
  });

  function toggleTheme() {
    dark = !dark;
    localStorage.setItem("theme", dark ? "dark" : "light");
    updateTheme();
  }

  function updateTheme() {
    // выполняется только на клиенте
    if (typeof document !== "undefined") {
      document.documentElement.classList.toggle("dark", dark);
    }
  }
</script>

<button on:click={toggleTheme} style="margin-top:auto; padding:0.5rem;">
  {#if dark}
    🌙 Тёмная
  {:else}
    ☀️ Светлая
  {/if}
</button>