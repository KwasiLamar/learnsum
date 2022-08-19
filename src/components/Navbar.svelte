<script lang="ts">
	import { supabase } from '$lib/supabaseClient';
	import { user } from '../stores/AuthStore';

	user.set(supabase.auth.user());

	supabase.auth.onAuthStateChange((_, session) => {
		user.set(session.user);
	});
</script>

<nav class="flex items-center justify-between flex-col md:flex-row md:p-2">
	<div>
		<h1 class="flex items-center justify-center text-lg flex-row-reverse">
			LearnSum
			<a href="/">
				<img src="/books.png" alt="LearnSum" class="h-auto w-14 m-2" />
			</a>
		</h1>
	</div>
	<div class="m-2">
		{#if $user}
			<a href="/profile">Welcome <span class="font-bold">Pernell</span></a>
			<a href="/signout" class="hover:text-sky-60 m-2 transition text-lg">Sign Out</a>
		{:else}
			<a href="/login" class="hover:text-sky-600 m-2 transition text-lg">Login</a>
			<a href="/register" class="hover:text-sky-600 m-2 transition text-lg">Register</a>
		{/if}
	</div>
</nav>
