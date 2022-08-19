<script lang="ts">
	import { supabase } from '$lib/SupabaseClient';
	import Showcase from '../components/Showcase.svelte';
	// async function get_username() {
	// 	const loggedInUserId = '4c7928a8-32b3-4f5f-9ca1-70a7920c2803';
	// 	let { data, error } = await supabase
	// 		.from('users')
	// 		.select('user_id, name')
	// 		.eq('user_id', loggedInUserId);
	// 	if (error) throw error;
	// 	console.log(data);
	// }
	// get_username();
</script>

<Showcase />
