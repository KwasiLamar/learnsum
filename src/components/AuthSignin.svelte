<script lang="ts">
	import { supabase } from '$lib/SupabaseClient';

	let loading = false;
	let email: string;
	let password: string;

	const handleLogin = async () => {
		try {
			loading = true;
			const { error } = await supabase.auth.signIn({ email, password });
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
	<h1 class="text-center text-2xl font-bold mb-4">Login to LearnSum</h1>
	<div class="flex flex-col">
		<input type="email" bind:value={email} placeholder="Email..." />
		<input type="password" bind:value={password} placeholder="Password" />
	</div>
	{#if loading}
		<button class="btn-blue block" disabled
			>Loading <i class="fas fa-spinner animate-spin" /></button
		>
	{:else}
		<button class="btn-blue block" type="submit">Submit</button>
	{/if}
</form>
