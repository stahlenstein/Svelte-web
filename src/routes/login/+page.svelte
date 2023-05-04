<script lang="ts">
  import { applyAction, enhance } from "$app/forms";
  import { pb } from "$lib/pocketbase";
  import "@picocss/pico";
</script>

<article class="grid" style="width: fit-content; margin: auto;">
  <div>
    <hgroup>
      <h1>Log in</h1>
      <h2>Placeholder text</h2>
    </hgroup>
    <form
      method="POST"
      use:enhance={() => {
        return async ({ result }) => {
          pb.authStore.loadFromCookie(document.cookie);
          await applyAction(result);
        };
      }}
    >
      <input type="email" name="email" placeholder="Email" />
      <input type="password" name="password" placeholder="Password" />
      <fieldset>
        <label for="remember">
          <input type="checkbox" role="switch" id="remember" name="remember" />
          Remember me
        </label>
      </fieldset>
      <button type="submit" style="width: auto;" class="contrast">Log in</button>
    </form>
  </div>
</article>
