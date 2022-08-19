<script lang="ts">
	import { supabase } from '$lib/SupabaseClient';
	import { goto } from '$app/navigation';

	let loading = false;
	let email: string;
	let password: string;
	let username: string;

	const handleLogin = async () => {
		try {
			loading = true;
			const { error } = await supabase.auth.signUp({ email, password });
			if (error) throw error;
			alert('Check your email for the login link!');
		} catch (error: any) {
			alert(error.error_description || error.message);
		} finally {
			loading = false;
		}
	};
</script>

<form class="flex flex-col justify-center" on:submit|preventDefault={handleLogin}>
	<h1 class="text-center text-2xl font-bold mb-4">Sign Up to LearnSum</h1>
	<div class="flex flex-col">
		<input type="text" bind:value={username} placeholder="Username..." />
		<input type="email" bind:value={email} placeholder="Email..." />
		<input type="password" bind:value={password} placeholder="Password" />
	</div>
	<button type="submit" class="btn-blue block">Submit</button>
</form>
