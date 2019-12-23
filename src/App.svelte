<script>
	import { onMount } from "svelte";
	import User from './User.svelte';
	import Navbar from './Navbar.svelte';
	import UserSearch from './UserSearch.svelte';

	let users;
	
	onMount(() => {
		getUsers();
	});

	function getUsers() {
		fetch("https://api.github.com/users")
		.then(resp => resp.json())
		.then(data => {
			//console.log(`Users: ${data}`);
			users = data;
		});
	}
</script>

<main>
    <Navbar/>
	<UserSearch />
	
	{#if users}
	  <ul class="user-list">
	    {#each users as user}
		<li>
		<a href="{user.html_url}" target="_blank">
		  <User username={user.login} repos={user.id} avatar={user.avatar_url} />
		</a> 
		</li>
		{/each}
	  </ul>
	{/if}
</main>

<style>

   .user-list {
	   display: grid;
	   grid-template-columns: repeat(5, auto);
	   grid-template-rows: auto;
	   grid-gap: 10px;
	   list-style-type: none;
   }


   a:link {
	   text-decoration: none;
	   color: brown;
   }
   a:visited {
	   color: darkolivegreen;
   }


    /* .user-list {
    display: flex;
    flex-flow: wrap;
    list-style: none;
    margin: 0;
    padding: 0;
  } */
   
	/* .user-list {
		display: grid;
		grid-template-columns: repeat(5, 0.1fr);
		grid-template-rows: 50px;
		grid-gap: 50px;
		list-style: none;
	} */

</style>