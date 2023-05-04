<script lang="ts">
  import { applyAction, enhance } from "$app/forms";
  import { currentUser, pb } from "$lib/pocketbase";
  import "@picocss/pico";
  import "../app.css";
  import { list } from "postcss";
</script>

<!-- Navigation Bar -->
<nav class="container-fluid" style="width: 95%">
  <ul>
    <li>
      <a class="contrast" href="./"
        ><strong>Floyd County Water Department</strong></a
      >
    </li>
  </ul>
  <ul>
    {#if $currentUser}
      <li><a href="/">{$currentUser.email}</a></li>
      <form
        style="margin-bottom: 0; padding-top: 20px; padding-left: 30px;"
        method="POST"
        action="/logout"
        use:enhance={() => {
          return async ({ result }) => {
            pb.authStore.clear();
            await applyAction(result);
          };
        }}
      >
        <button type="submit" class="secondary outline" style="padding: .5rem">Log out</button>
      </form>
    {:else}
      <li><a role="button" href="/login">Log in</a></li>
      <li><a href="/register">Register</a></li>
    {/if}
  </ul>
</nav>
{#if $currentUser}
<nav class="container-fluid" style="background: var(--code-background-color); width: 90%; border-radius: .5rem;">
  <ul>
    <li><h6 style="margin-bottom: 0; margin-right: 3rem">Welcome, {$currentUser.username}</h6></li>
    <li><a href="/table" class="secondary"><u>Meter Table</u></a></li>
    <li><a href="/posts" class="secondary"><u>Posts</u></a></li>
    <li><a href="/map" class="secondary"><u>Map</u></a></li>
  </ul>
</nav>
{/if}

<!-- Main Area -->

<main class="container-fluid" style="width: 95%; position: sticky;">
  <slot />
</main>

<!-- Footer -->

<footer class="container-fluid" style="padding-top: 0; padding-bottom: 1%; position: fixed; bottom: 0px">
  <small>Floyd County Water Department</small>
</footer>
