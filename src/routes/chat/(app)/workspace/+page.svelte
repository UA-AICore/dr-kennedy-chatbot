<script lang="ts">
	import { goto } from '$app/navigation';
	import { user } from '$lib/stores';
	import { onMount } from 'svelte';

	onMount(() => {
		if ($user?.role !== 'admin') {
			if ($user?.permissions?.workspace?.models) {
				goto('/chat/workspace/models');
			} else if ($user?.permissions?.workspace?.knowledge) {
				goto('/chat/workspace/knowledge');
			} else if ($user?.permissions?.workspace?.prompts) {
				goto('/chat/workspace/prompts');
			} else if ($user?.permissions?.workspace?.tools) {
				goto('/chat/workspace/tools');
			} else {
				goto('/chat/');
			}
		} else {
			goto('/chat/workspace/models');
		}
	});
</script>
