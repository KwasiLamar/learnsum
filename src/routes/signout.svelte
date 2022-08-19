<script lang="ts">
	import { goto } from '$app/navigation';
	import { supabase } from '$lib/SupabaseClient';

	async function signOut() {
		try {
			const { error } = await supabase.auth.signOut();
			if (error) return error;
			goto('/login');
		} catch (error) {
			alert(error.message);
		}
	}
	signOut();
</script>
