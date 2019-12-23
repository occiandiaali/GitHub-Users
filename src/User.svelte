<script>
  export let username;
  export let avatar;
  export let repos;
</script>

<div class="user">
  <img src="{avatar}" alt="{username}'s Avatar"/>
  <h3>{username} - ({repos}) repos</h3>
</div>

<style>
  .user {
    padding: 5px;
    margin: 3px;
    border: 1px solid #ddd;
    box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.1);
    border-radius: 5px;
    text-align: center;
    background: goldenrod;
  }

  img {
    border-radius: 5px;
    max-width: 180px;
    height: 180px;
    margin-top: 2em;
  }

  h3 {
    font-size: 16px;
    margin: 0;
  }
</style>