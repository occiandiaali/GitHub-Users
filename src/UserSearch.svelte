<script>
  import User from './User.svelte';


  let usernameQuery = "";
  let user;

  function handleSubmit(e) {
      e.preventDefault();

      fetch(`https://api.github.com/users/${usernameQuery}`)
      .then(resp => resp.json())
      .then(data => (user = data));
      usernameQuery = ""
  }
</script>

<style>
  .user-search {
      text-align: center;
  }

  a:link {
      text-decoration: none;
  }
</style>

<section class="user-search">
  <h2>Search for Users</h2>

  <form on:submit={handleSubmit}>
    <input type="text"  placeholder="github username.." bind:value={usernameQuery}/>
    <button>Search</button>
  </form>
  {#if user}
    <a href="{user.html_url}" target="_blank">
    <User username={user.login} avatar={user.avatar_url} repos={user.id}/>
    </a>
  {/if}
</section>