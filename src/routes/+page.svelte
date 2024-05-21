<script lang="ts">
	import type { PageData } from './$types';
	import Google from '$lib/components/icons/Google.svelte';
	import { Avatar } from '@skeletonlabs/skeleton-svelte';
	export let data: PageData;
	let avatarsrc = `https://unavatar.io/${data.user?.email}`;
</script>

<div class="flex h-screen w-full flex-col items-center justify-center gap-2">
	<h1 class="text-xl">Skirt!</h1>

	{#if data.authenticated}
		<p>
			You are logged in as <span class="font-bold">{data.user?.email}</span><Avatar
				src={avatarsrc}
			></Avatar>
		</p>
		<a class="btn preset-filled-primary-500" href="/auth/logout">Logout</a>
	{:else}
		<a class="btn preset-filled-primary-500" href="/auth/google"><Google /> Login</a>
	{/if}
</div>
