<script lang="ts">
	import { onMount } from 'svelte';
	import { supabase } from '$lib/SupabaseClient';
	let username = '';
	onMount(async () => {
		async function updateProfile() {
			const user = supabase.auth.user();
			const updates = {
				id: user.id,
				username,
				updated_at: new Date()
			};

			let { error } = await supabase.from('profiles').upsert(updates);
			if (error) {
				throw error;
			}
		}
		updateProfile();
		const getProfile = async () => {
			const user: any = supabase.auth.user();
			if (user) {
				console.log(user.id);
				const { data, error } = await supabase
					.from('profiles')
					.select('username')
					.eq('id', user.id);
				console.log(user.id);
				if (error) return error;
				console.log(data);
			}
		};
		getProfile();
	});
</script>

<h1>{username}</h1>
